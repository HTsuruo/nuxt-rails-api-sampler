FROM ruby:2.7.0
RUN apt-get update && apt-get install -y apt-utils vim
RUN mkdir -p /nuxt-rails-api-sampler/backend
WORKDIR /nuxt-rails-api-sampler/backend
COPY Gemfile /nuxt-rails-api-sampler/backend/Gemfile
COPY Gemfile.lock /nuxt-rails-api-sampler/backend/Gemfile.lock
RUN bundle install -j4
ENV DOCKER=true
ENV LANG=C.UTF-8
COPY . /nuxt-rails-api-sampler/backend
# RUN mkdir -p tmp/sockets
