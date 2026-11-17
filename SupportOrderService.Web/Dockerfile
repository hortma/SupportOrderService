# Build the application from the repository root so project references are available.
FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
ARG BUILD_CONFIGURATION=Release
WORKDIR /src

# Copy source before restore so .NET 10 includes the implicit Blazor framework static assets.
COPY ["SupportOrderService.Web/SupportOrderService.Web.csproj", "SupportOrderService.Web/"]
COPY ["SupportOrderService.Core/SupportOrderService.Core.csproj", "SupportOrderService.Core/"]
COPY ["SupportOrderService.Infrastructure/SupportOrderService.Infrastructure.csproj", "SupportOrderService.Infrastructure/"]
COPY . .
RUN dotnet restore "SupportOrderService.Web/SupportOrderService.Web.csproj"

WORKDIR "/src/SupportOrderService.Web"
RUN dotnet build "SupportOrderService.Web.csproj" -c $BUILD_CONFIGURATION --no-restore -o /app/build

FROM build AS publish
ARG BUILD_CONFIGURATION=Release
RUN dotnet publish "SupportOrderService.Web.csproj" -c $BUILD_CONFIGURATION --no-restore -o /app/publish /p:UseAppHost=false

FROM mcr.microsoft.com/dotnet/aspnet:10.0 AS final
WORKDIR /app
EXPOSE 8080

ENV ASPNETCORE_HTTP_PORTS=8080

COPY --from=publish /app/publish .
USER $APP_UID
ENTRYPOINT ["dotnet", "SupportOrderService.Web.dll"]
