FROM ruby:3.1.2

ENV LANG C.UTF-8
ENV TZ Asia/Tokyo

RUN gem install bundler \
  rubocop \
  rubocop-rails \
  rubocop-performance

# yarnをインストールする
RUN apt-get install apt-transport-https
RUN curl https://deb.nodesource.com/setup_14.x | bash
RUN curl https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-get update -qq && \
    apt-get install -y --force-yes \
              build-essential \
              nodejs \
              yarn


RUN mkdir -p ~/.ssh && ln -s /run/secrets/host_ssh_key ~/.ssh/id_rsa

RUN echo 'eval `ssh-agent`' >> ~/.bashrc
RUN echo 'ssh-add ~/.ssh/id_rsa' >> ~/.bashrc
