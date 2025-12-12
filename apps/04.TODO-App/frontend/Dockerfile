FROM node:lts-bookworm-slim AS development

WORKDIR /usr/src/app

COPY package.json package-lock.json ./
RUN npm ci

COPY . .

EXPOSE 3000
CMD ["npm", "start"]

FROM development AS dev-envs

RUN useradd -s /bin/bash -m vscode \
    && groupadd docker \
    && usermod -aG docker vscode

COPY --from=gloursdocker/docker / /

CMD ["npm", "start"]
