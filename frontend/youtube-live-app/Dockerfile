FROM node:21-alpine3.18 AS builder
WORKDIR /devops-na-nuvem-week-live
COPY . .
RUN npm ci --silent
RUN npm run build
RUN npm prune --omit=dev

FROM node:21-alpine3.18 AS runner
WORKDIR /devops-na-nuvem-week-live
COPY --from=builder /devops-na-nuvem-week-live/.next /devops-na-nuvem-week-live/.next
COPY --from=builder /devops-na-nuvem-week-live/node_modules /devops-na-nuvem-week-live/node_modules
COPY --from=builder /devops-na-nuvem-week-live/package.json /devops-na-nuvem-week-live/package.json
COPY --from=builder /devops-na-nuvem-week-live/public /devops-na-nuvem-week-live/public

ENV PORT 80
EXPOSE 80
ENTRYPOINT ["npm", "start"]