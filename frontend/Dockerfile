########################
# Build stage
########################
FROM node:20-alpine AS build
WORKDIR /src

# copy dependency manifest
COPY package*.json ./

# install deps (CI = deterministic)
RUN npm ci

# copy source code
COPY . .

# build
RUN npm run build


########################
# Runtime stage
########################
FROM nginx:alpine
COPY --from=build /src/dist /usr/share/nginx/html

