FROM nginx

# Copy works
COPY ./public /usr/share/nginx/html

# This doesn't work:
# VOLUME ['./public:/usr/share/nginx/html:ro']

# This doesn't work
# VOLUME ['public']
# RUN rm -rf /usr/share/nginx/html
# RUN ln -s /public /usr/share/nginx/html
