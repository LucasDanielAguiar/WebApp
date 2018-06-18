# ProjectoSW
This is a example of a Web App CRUD on ASP.NET core to test in Docker.

INSTRUCTIONS TO RUN THE APP ON DOCKER

you must ensure that you have a file without an extension called “DockerFile” and that you must have this inside:

FROM microsoft/aspnetcore-build:2.0 AS build-env
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish -c Release -o out

FROM microsoft/aspnetcore:2.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "aspnetapp.dll"]


an other file called “archivo.Dockerignore” and that you must have this inside:

bin\
obj\


Once verified that, open the console of Windows (in the Windows search, write CMD and press ENTER) and navigate to your proyect.
Once you get there, write de following commands:

-> docker build -t WebApp .

-> docker run -d -p 8080:80 --name myapp WebApp


Now all you have to do is to open your browser and type in the address bar:

localhost:8080




I hope you'll be helped, Good Luck!!
