# URL Shortener Service

An ASP.NET MVC 5 sample application for creating and tracking shortened URLs.

## Tech Stack

- C#
- ASP.NET MVC 5
- Entity Framework 6 (Code First + Migrations)
- SQL Server LocalDB
- .NET Framework 4.5
- Bootstrap
- jQuery

## Features

- Create short URLs from long URLs
- Redirect from short URL to original URL
- Reuse existing short URL for duplicate long URLs
- Track click count per short URL
- Capture basic request statistics (browser, language, referrer, host address, mobile flag)
- User authentication support with per-user URL listing

## Requirements

- Windows with Visual Studio (2013 or newer) and ASP.NET/.NET Framework web tooling
- .NET Framework 4.5 targeting pack
- SQL Server LocalDB
- NuGet Package Manager

## Getting Started

1. Open `ShortURLService.sln` in Visual Studio.
2. Restore NuGet packages (right click solution -> `Restore NuGet Packages`).
3. Verify or update the connection string in `ShortURLService/Web.config`:
   - `UrlContext` defaults to `(LocalDb)\v11.0`
4. Open Package Manager Console and run:
   - `Update-Database`
5. Build and run the `ShortURLService` project.
6. Open the app URL shown by Visual Studio (default is `http://localhost:2177/`).

## How It Works

- `POST /Home/ShorterURL` accepts a long URL and returns JSON with a generated short URL.
- `GET /{shortCode}` resolves the short code and redirects to the original URL.
- URL records are stored in `Urls`, and visit metadata is stored in `UrlStats`.

## Project Structure

- `ShortURLService/Controllers` - MVC controllers and request handling
- `ShortURLService/Models` - URL and statistics models
- `ShortURLService/DAL` - Entity Framework context
- `ShortURLService/Migrations` - EF Code First migrations
- `ShortURLService/Views` - Razor views

## Notes

- This is a legacy .NET Framework project and is not SDK-style.
- `URL.CheckLongUrlExists()` performs a live HTTP HEAD request before storing URLs.
- If LocalDB `v11.0` is unavailable on your machine, update `UrlContext` in `Web.config` to your installed LocalDB instance.
