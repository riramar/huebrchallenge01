FROM nginx:mainline-alpine
RUN rm /etc/nginx/conf.d/*
ADD huebrchallenge01.conf /etc/nginx/conf.d/
ADD index.html /usr/share/nginx/html/
ADD flag.html /usr/share/nginx/html/
