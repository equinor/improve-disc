FROM squidfunk/mkdocs-material as BUILD
WORKDIR /mkdocs

COPY . .
RUN pip3 install -r docs/cam/requirements.txt
RUN mkdocs build -f docs/cam/mkdocs.yml

FROM nginxinc/nginx-unprivileged:latest
COPY --from=BUILD ./mkdocs/docs/cam/site ./usr/share/nginx/html

USER 1000

EXPOSE 8080