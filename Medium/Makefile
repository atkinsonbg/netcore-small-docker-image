publish:
	dotnet publish -r linux-musl-x64 -p:PublishSingleFile=true -c Release -o ./deploy

run:
	dotnet run

docker:
	docker build -t netcore-small-docker-image .

dockerrun:
	docker run -p 80:5000 netcore-small-docker-image:latest