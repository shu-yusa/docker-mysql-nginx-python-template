FROM nginx
MAINTAINER yusa
ADD server.conf /etc/nginx/conf.d/default.conf
ADD nginx.conf /etc/nginx/nginx.conf

RUN apt-get update
RUN apt-get install -y vim
ADD vimrc /root/.vimrc
RUN echo "alias ls='ls -hp'" >> /root/.bashrc
RUN echo "alias ll='ls -l'" >> /root/.bashrc
RUN echo "alias la='ls -la'" >> /root/.bashrc
