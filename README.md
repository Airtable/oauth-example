# OAuth-Example

Example code for authorizing a user an Airtable OAuth integration.

This code example is intended for Mac and Linux users. Windows developers may need to adjust the setup instructions slightly.

Setup instructions

1. Install [nodejs](https://nodejs.org/en/) (this repo is tested with node16).
2. From the project root directory run `npm i` to install the dependencies.
3. Go to https://airtable.com/create/oauth and register a new integration. Set the redirect URL to http://localhost:4000/airtable-oauth (if you choose a different path or port you will need to edit the code).
4. run `touch ./.config.js` to create a `.config.js` file, then copy paste the following contents into it:
    ```typescript
    const config = {
        // Uses the PORT variable declared here, the path is defined in code
        port: 4000,
        redirectUri: 'http://localhost:4000/airtable-oauth',
        clientId: INSERT_YOUR_CLIENT_ID,
        // If you're not using a client secret, set to the empty string: ""
        clientSecret: INSERT_YOUR_CLIENT_SECRET,
        airtableUrl: 'https://www.airtable.com',
        // space delimited list of Airtable scopes, update to the list of scopes you want for your integration
        scope: 'data.records:read data.records:write',
    };
    module.exports = config;
    ```
5. within `./.config.js` (the file you created) fill in your `client_id`, desired `scopes`, and `client_secret` (if applicable).
6. From the project root directory run `npm start` to begin running the service. You should see "Example app listening on port 4000" in your console. Note that if you change the values in `./.config.js` you'll need to restart this process, any other changes to the code should be hot-reloaded when saving.

Creating a token:

1. Ensure the process is running and configured with your credentials in `./.config.js`
2. Visit `http://localhost:4000/` and click the link to authorize your integration
3. Add your desired resources, then click authorize.
4. The response, including your access token and refresh token, should be visible

Refreshing a token:
1. Ensure the process is running and configured with your credentials in `./.config.js`
2. Ensure you have a refresh token (obtainable by creating a token, see above)
3. Visit `http://localhost:4000/` and enter your refresh token to the input field and click "submit"
4. The response, including your new access token and refresh token, should be visible


You can read more [in the docs](https://airtable.com/oauth-beta-developer-reference).
