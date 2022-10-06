# OAuth-Example
Example code for authorizing a user an Airtable OAuth integration.

This code example is intended for Mac and Linux users. Windows developers may need to adjust the setup instructions slightly.

Setup instructions
1. Install [nodejs](https://nodejs.org/en/) (this repo is tested with node16).
2. From the project root directory run ```npm i``` to install the dependencies.
3. run ```touch ./.env``` to create a `.env` file, then copy paste the following contents into it:
    ```
    PORT=4000
    # Uses the PORT variable declared here, the path is defined in code
    REDIRECT_URI=http://localhost:4000/airtable-oauth
    CLIENT_ID=INSERT_YOUR_CLIENT_ID
    # Leave client_secret empty if you have no client_secret (nothing after the =)
    CLIENT_SECRET=INSERT_YOUR_CLIENT_SECRET
    AIRTABLE_BASE_URL=https://www.airtable.com
    # space delimited list of Airtable scopes, update to the list of scopes
    # you want for your integration
    SCOPE=data.records:read data.records:write
    ```
4. Go to https://www.airtable.com/oauth/create and register a new integration. Set the redirect URL to http://localhost:4000/airtable-oauth (if you choose a different path or port you will need to edit the code).
5. within `./.env` (the file you created) fill in your `client_id`, desired `scopes`, and `client_secret` (if applicable).
6. From the project root directory run ```npm start``` to begin running the service. You should see "Example app listening on port 4000" in your console. Note that if you change the values in `./env` you'll need to restart this process, any other changes to the code should be hot-reloaded when saving.


Creating a token:
1. Ensure the process is running and configured with your credentials in `./.env`
2. Visit `http://localhost:4000/` and click "Testify!", this should bring you to the authorization screen
3. Add your desired resources, then click authorize.
4. Your OAuth Access token should be viewable in the terminal running the server

You can read more [in the docs](https://airtable.com/oauth-beta-developer-reference).
