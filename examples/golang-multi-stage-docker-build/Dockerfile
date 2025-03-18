###########################################
# BASE IMAGE : Stage 1
###########################################

FROM ubuntu AS build      # create base img as ubuntu, alias = build

RUN apt-get update && apt-get install -y golang-go    # check updates & install golang on ubutu base img

ENV GO111MODULE=off      #  turn off this Golang module

COPY . .                 # copy the S-code  (Copies the contents of the current dir (.) from the host machine to the current dir (.) in the Docker container)

RUN CGO_ENABLED=0 go build -o /app .  # build & create a binary exe file of our application & name it /app inside the docker img

############################################################
# HERE STARTS THE MAGIC OF MULTI STAGE BUILD : Stage 2
############################################################

FROM scratch  # create a minimal Docker image, starting with an empty base image. Docker image will not contain any OS files, libraries, utilities by default. It's up to us to copy over any necessary binaries or files. --> Golang specific

# Copy the compiled binary from the build stage [Stage 1 ]
COPY --from=build /app /app  # copy --form=build /source /destionation

# Set the entrypoint for the container to run the binary
ENTRYPOINT ["/app"]    # default executable = /app (or binary) that will run when the container starts


