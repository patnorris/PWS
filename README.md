# PersonalWebSpace

Welcome to your new PersonalWebSpace project and to the internet computer development community. By default, creating a new project adds this README and some template files to your project directory. You can edit these template files to customize your project and to include your own code to speed up the development cycle.

To get started, you might want to explore the project directory structure and the default configuration file. Working with this project in your development environment will not affect any production deployment or identity tokens.

To learn more before you start working with PersonalWebSpace, see the following documentation available online:

- [Quick Start](https://sdk.dfinity.org/docs/quickstart/quickstart-intro.html)
- [SDK Developer Tools](https://sdk.dfinity.org/docs/developers-guide/sdk-guide.html)
- [Motoko Programming Language Guide](https://sdk.dfinity.org/docs/language-guide/motoko.html)
- [Motoko Language Quick Reference](https://sdk.dfinity.org/docs/language-guide/language-manual.html)
- [JavaScript API Reference](https://erxue-5aaaa-aaaab-qaagq-cai.raw.ic0.app)

If you want to start working on your project right away, you might want to try the following commands:

```bash
cd PersonalWebSpace/
dfx help
dfx canister --help
```

## Running the project locally

If you want to test your project locally, you can use the following commands:

```bash
# Starts the replica, running in the background
dfx start --background

# Install dependencies
npm install

# Deploys your canisters to the replica and generates your candid interface
Local:
dfx deploy --argument "(
  principal\"$(dfx identity get-principal)\",
  record {
    logo = record {
      logo_type = \"image/png\";
      data = \"\";
    };
    name = \"PersonalWebSpace\";
    symbol = \"PWS\";
    maxLimit = 65535;
  }
)"

dfx deploy --network ic --argument "(
  principal\"$(dfx identity get-principal)\",
  record {
    logo = record {
      logo_type = \"image/png\";
      data = \"\";
    };
    name = \"PersonalWebSpace\";
    symbol = \"PWS\";
    maxLimit = 65535;
  }
)"
```

Once the job completes, your application will be available at `http://localhost:8000?canisterId={asset_canister_id}`.

Additionally, if you are making frontend changes, you can start a development server with

```bash
npm start
```

Which will start a server at `http://localhost:8080`, proxying API requests to the replica at port 8000.

Top up cycles:
dfx identity --network=ic get-wallet
dfx wallet --network ic balance
dfx canister --network ic status PersonalWebSpace_backend
dfx canister --network ic status PersonalWebSpace_frontend
dfx canister --network ic --wallet 3v5vy-2aaaa-aaaai-aapla-cai deposit-cycles 3000000000000 PersonalWebSpace_backend
dfx canister --network ic --wallet 3v5vy-2aaaa-aaaai-aapla-cai deposit-cycles 300000000000 PersonalWebSpace_frontend

### Note on frontend environment variables

If you are hosting frontend code somewhere without using DFX, you may need to make one of the following adjustments to ensure your project does not fetch the root key in production:

- set`NODE_ENV` to `production` if you are using Webpack
- use your own preferred method to replace `process.env.NODE_ENV` in the autogenerated declarations
- Write your own `createActor` constructor

### Dev Notes
need to use single quotes in HTML to store as Text (which has double quotes)
remove all newlines and other space (used for exampleString): https://www.textfixer.com/tools/remove-line-breaks.php