FROM mcr.microsoft.com/dotnet/sdk:7.0-alpine AS builder
WORKDIR /devops-na-nuvem-week-live
COPY . .
RUN dotnet publish -c Release -o publish /devops-na-nuvem-week-live/YoutubeLiveApp.csproj

FROM mcr.microsoft.com/dotnet/aspnet:7.0-alpine AS runner
WORKDIR /devops-na-nuvem-week-live
COPY --from=builder /devops-na-nuvem-week-live/publish /devops-na-nuvem-week-live/publish
ENV PORT 80
ENV URLS http://0.0.0.0:80
EXPOSE 80
ENTRYPOINT ["dotnet", "/devops-na-nuvem-week-live/publish/YoutubeLiveApp.dll"]
