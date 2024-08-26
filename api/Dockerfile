FROM node:18-slim

WORKDIR /usr/src/app

# COPY package.json yarn.lock .yarnrc.yml ./
# COPY .yarn ./.yarn

COPY package.json ./

# Install dependencies
RUN yarn install

COPY . .

RUN yarn build

EXPOSE 3000

CMD ["yarn", "run", "start"]