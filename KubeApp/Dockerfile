FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.1-sdk
WORKDIR /src
COPY . .
RUN dotnet publish KubeApp.csproj -c Release -o /app
WORKDIR /app
COPY /app .
RUN dotnet build "KubeApp.csproj" -c Release -o /app

FROM microsoft/dotnet:2.1-aspnetcore-runtime 
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "KubeApp.dll"]
