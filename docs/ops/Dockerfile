FROM squidfunk/mkdocs-material as BUILD
WORKDIR /mkdocs

COPY . .
RUN pip3 install -r docs/ops/requirements.txt
RUN mkdocs build -f docs/ops/mkdocs.yml

FROM nginxinc/nginx-unprivileged:latest
COPY --from=BUILD ./mkdocs/docs/ops/site ./usr/share/nginx/html

USER 1000

EXPOSE 8080