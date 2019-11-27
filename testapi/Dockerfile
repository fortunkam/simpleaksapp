FROM mcr.microsoft.com/dotnet/core/aspnet:3.0 AS base
WORKDIR /app
EXPOSE 8080

FROM mcr.microsoft.com/dotnet/core/sdk:3.0 AS build
WORKDIR /src
COPY ["testapi.csproj", "./"]
RUN dotnet restore "./testapi.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "testapi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "testapi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "testapi.dll"]
