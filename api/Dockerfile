# Build
FROM node:18 AS build

WORKDIR /usr/src/app

# COPY package.json yarn.lock .yarnrc.yml ./
# COPY .yarn ./.yarn

COPY package.json ./

# Install dependencies
RUN yarn install

COPY . .

RUN yarn run build
# RUN yarn workspaces focus --production && yarn cache clean

# Production
FROM node:18-alpine3.19

WORKDIR /usr/src/app

COPY --from=build /usr/src/app/dist ./dist
COPY --from=build /usr/src/app/node_modules ./node_modules

EXPOSE 3000

CMD ["yarn", "run", "start"]