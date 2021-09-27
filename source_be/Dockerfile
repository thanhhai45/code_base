FROM ruby:2.7.3

ENV RAILS_ENV=development
ENV NODE_ENV=development
ENV RACK_ENV=development
ENV MALLOC_ENV=development

RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs
RUN mkdir -p /usr/src/backend-app
WORKDIR /usr/src/backend-app
COPY Gemfile /usr/src/backend-app/Gemfile
COPY Gemfile.lock /usr/src/backend-app/Gemfile.lock
RUN bundle install
COPY . /usr/src/backend-app

COPY ./docker-entrypoint.sh /
RUN chmod +x /docker-entrypoint.sh

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["rails", "s", "-p", "3001", "-b", "0.0.0.0"]