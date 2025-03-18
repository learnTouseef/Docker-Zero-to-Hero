###########################################
# BASE IMAGE
###########################################

FROM ubuntu AS build  # create base img as ubuntu, alias = build

RUN apt-get update && apt-get install -y golang-go    # check updates & install golang on ubutu base img

ENV GO111MODULE=off      # turn off this Golang module

COPY . .                 # copy the S-code  (Copies the contents of the current dir (.) from the host machine to the current dir (.) in the Docker container)

RUN CGO_ENABLED=0 go build -o /app .  # build & create a binary exe file of our application & name it /app inside the docker img

ENTRYPOINT ["/app"]  # default executable = /app (or binary) that will run when the container starts --> run our app

