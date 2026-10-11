FROM ruby:3.3-slim

WORKDIR /app

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
       build-essential libpq-dev \
    && rm -rf /var/lib/apt/lists/*

COPY Gemfile Gemfile.lock ./

RUN gem install bundler \
    && bundle install

COPY app.rb ./

EXPOSE 8086

CMD ["bundle", "exec", "ruby", "app.rb"]
