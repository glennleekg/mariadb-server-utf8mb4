FROM mariadb/server:10.3

RUN \
  touch /etc/mysql/mariadb.conf.d/charset.cnf \
  && printf " \
  [client]\n \
  default-character-set = utf8mb4\n \
  \n \
  [mysqld]\n \
  character-set-server  = utf8mb4\n \
  collation-server      = utf8mb4_unicode_ci\n \
  character_set_server  = utf8mb4\n \
  collation_server      = utf8mb4_unicode_ci\n" \
  >> /etc/mysql/mariadb.conf.d/charset.cnf

ARG user=developer
ARG group=developer
ARG home=/home/$user
ARG project=projects/project

RUN \
  groupadd $group \
  && useradd -m -g $group $user

USER $user

RUN mkdir -p $home/$project

WORKDIR $home/$project

USER root

CMD ["mysqld"]