# pload2

This project was created using create-payload-app using the blog template.

## How to Use

`yarn dev` will start up your application and reload on any changes.

## Steps to reproduce

- I set up a new MongoDB database
- Checked the node version was 18+ (18.5.0)
- Installed a new project via npx create-payload-app and selected the blog template
- Followed instructions to install three extra packages: 
  - @payloadcms/db-mongodb
  - @payloadcms/richtext-slate
  - @payloadcms/bundler-webpack
- Added *editor* and *db* settings to payload.config.ts
- Did not attempt to migrate any custom settings or overrides from the other projects. I just wanted to try out Payload 2 on my local and then selectively migrate custom settings later. 
- Ran `yarn dev`

I encountered the followed error:

```bash
/Users/neil/Sites/platform3/rca/payload/pl2/v2/pload2/node_modules/payload/src/express/admin.ts:8
      ctx.express.use(ctx.config.routes.admin, await ctx.config.admin.bundler.dev(ctx))
                                                                              ^
TypeError: Cannot read properties of undefined (reading 'dev')
    at initAdmin (/Users/neil/Sites/platform3/rca/payload/pl2/v2/pload2/node_modules/payload/src/express/admin.ts:8:79)
    at initHTTP (/Users/neil/Sites/platform3/rca/payload/pl2/v2/pload2/node_modules/payload/src/initHTTP.ts:59:20)
    at processTicksAndRejections (node:internal/process/task_queues:95:5)
    at Payload.init (/Users/neil/Sites/platform3/rca/payload/pl2/v2/pload2/node_modules/payload/src/index.ts:17:21)
```

### Docker

If you have docker and docker-compose installed, you can run `docker-compose up`

To build the docker image, run `docker build -t my-tag .`

Ensure you are passing all needed environment variables when starting up your container via `--env-file` or setting them with your deployment.

The 3 typical env vars will be `MONGODB_URI`, `PAYLOAD_SECRET`, and `PAYLOAD_CONFIG_PATH`

`docker run --env-file .env -p 3000:3000 my-tag`
