FROM mcr.microsoft.com/dotnet/core/sdk as BUILD
WORKDIR /api
COPY . .
RUN dotnet publish -r linux-musl-x64 -p:PublishSingleFile=true -c Release -o ./deploy

FROM mcr.microsoft.com/dotnet/core/runtime-deps:3.1.0-alpine3.10
WORKDIR /api
RUN addgroup -S mediumgroup && \
    adduser -S mediumuser
USER mediumuser
COPY --from=BUILD --chown=mediumuser:mediumgroup api/deploy/Medium medium
ENV ASPNETCORE_URLS=http://+:5000
CMD ["./medium"]