FROM mcr.microsoft.com/dotnet/framework/sdk:4.8 AS build
WORKDIR /app
#COPY *.sln .
#COPY src/FunnyQuotesLegacyService/*.csproj ./FunnyQuotesLegacyService/
#COPY src/FunnyQuotesLegacyService/*.config ./FunnyQuotesLegacyService/
WORKDIR /app/src
COPY ./ .
WORKDIR /app/src
RUN msbuild -t:restore -p:RestorePackagesConfig=true
RUN msbuild 


FROM mcr.microsoft.com/dotnet/framework/aspnet:4.8 AS runtime
WORKDIR /inetpub/wwwroot
COPY --from=build /app/src/FunnyQuotesUIForms/. ./