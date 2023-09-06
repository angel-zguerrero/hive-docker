FROM ubuntu:20.04
RUN apt-get update && apt-get install -y curl gnupg
RUN apt-key adv -q --keyserver "hkp://keyserver.ubuntu.com:80" --recv-keys "F77F1EDA57EBB1CC"
RUN apt-get install -y erlang-nox erlang-dev build-essential git
RUN echo "deb https://dl.bintray.com/rabbitmq/debian focal main" | tee /etc/apt/sources.list.d/bintray.rabbitmq.list
RUN echo "deb http://ppa.launchpad.net/erlang-solutions/ppa/ubuntu focal main" | tee /etc/apt/sources.list.d/erlang.list
RUN  apt-get install -y rabbitmq-server && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN curl -sSL 'https://github.com/noxdafox/rabbitmq-message-deduplication/releases/download/0.4.5/elixir-1.8.2.ez' > /usr/lib/rabbitmq/lib/rabbitmq_server-3.8.2/plugins/elixir-1.8.2.ez
RUN curl -sSL 'https://github.com/noxdafox/rabbitmq-message-deduplication/releases/download/0.4.5/rabbitmq_message_deduplication-v3.8.x_0.4.5.ez' > /usr/lib/rabbitmq/lib/rabbitmq_server-3.8.2/plugins/rabbitmq_message_deduplication-3.8.2.ez
RUN rabbitmq-plugins enable --offline rabbitmq_message_deduplication
RUN rabbitmq-plugins enable --offline rabbitmq_management
EXPOSE 15672 5672
CMD ["rabbitmq-server"]