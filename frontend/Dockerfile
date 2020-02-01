FROM node:11.14.0-alpine
WORKDIR /nuxt-rails-api-sampler/frontend
RUN apk update && \
    apk upgrade && \
    npm install -g npm && \
    npm install -g @vue/cli && \
    npm install -g create-nuxt-app
ENV HOST 0.0.0.0
EXPOSE 3000
