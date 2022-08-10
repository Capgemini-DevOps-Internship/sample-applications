FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build-env
WORKDIR /apps/sample-applications/booking-api/Booking.Server

# Copy everything
COPY . ./
RUN dotnet restore
# Build and publish a release
RUN dotnet publish -c Release -o out

# Build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /apps/sample-applications/booking-api/Booking.Server
COPY --from=build-env /apps/sample-applications/booking-api/Booking.Server .
ENTRYPOINT ["dotnet", "Booking.Server.API.dll", "Booking.Server.DB.dll", "Booking.Server.Test.dll"]

