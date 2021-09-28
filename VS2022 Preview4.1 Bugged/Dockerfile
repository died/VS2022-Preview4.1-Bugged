#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["VS2022 Preview4.1 Bugged/VS2022 Preview4.1 Bugged.csproj", "VS2022 Preview4.1 Bugged/"]
RUN dotnet restore "VS2022 Preview4.1 Bugged/VS2022 Preview4.1 Bugged.csproj"
COPY . .
WORKDIR "/src/VS2022 Preview4.1 Bugged"
RUN dotnet build "VS2022 Preview4.1 Bugged.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "VS2022 Preview4.1 Bugged.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "VS2022 Preview4.1 Bugged.dll"]