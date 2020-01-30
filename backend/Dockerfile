FROM ruby:2.7.0
RUN apt-get update && apt-get install -y apt-utils vim
RUN mkdir -p /nuxt-rails-api-sampler
WORKDIR /nuxt-rails-api-sampler
COPY Gemfile /nuxt-rails-api-sampler/Gemfile
COPY Gemfile.lock /nuxt-rails-api-sampler/Gemfile.lock
RUN bundle install -j4
ENV DOCKER=true
ENV LANG=C.UTF-8
COPY . /nuxt-rails-api-sampler
# RUN mkdir -p tmp/sockets
