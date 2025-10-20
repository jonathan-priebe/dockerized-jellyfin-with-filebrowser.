# 📺 Jellyfin + FileBrowser Stack

A simple Docker Compose setup for running [Jellyfin](https://jellyfin.org/) alongside two [FileBrowser](https://filebrowser.org/) instances for managing TV shows and movies.

## 📑 Table of Contents

- [Prerequisites](#prerequisites)
- [Quickstart](#quickstart)
- [Usage](#usage)
- [Volumes](#volumes)
- [Author](#author)

## ✅ Prerequisites

- Docker & Docker Compose installed
- UID/GID 1000 should match your local user (adjust if needed)
- Basic understanding of container volumes and networking

## ⚡ Quickstart

1. **Clone the repository**
   ```bash
   git clone https://github.com/jonathan-priebe/dockerized-jellyfin-with-filebrowser
   cd dockerized-jellyfin-with-filebrowser
   ```

2. **Start the stack**
   ```bash
   docker compose up -d
   ```

3. **Fix permissions for FileBrowser access**  
   Ensure FileBrowser can read/write inside the volumes:
   ```bash
   sudo chown -R 1000:1000 /var/lib/docker/volumes/jellyfin_jellyfin-tvseries/_data/
   sudo chown -R 1000:1000 /var/lib/docker/volumes/jellyfin_jellyfin-movies/_data/
   ```

## 🎬 Usage

- **Jellyfin Media Server**  
  Access via [http://localhost:8096](http://localhost:8096)  
  Add media libraries from `/data/tvshows` and `/data/movies`

- **FileBrowser for TV Shows**  
  Access via [http://localhost:3002](http://localhost:3002)  
  Manage files in `jellyfin-tvseries` volume

- **FileBrowser for Movies**  
  Access via [http://localhost:3003](http://localhost:3003)  
  Manage files in `jellyfin-movies` volume

## 📦 Volumes

| Volume Name           | Purpose                  |
|-----------------------|--------------------------|
| jellyfin-library      | Jellyfin config & cache  |
| jellyfin-tvseries     | TV show media files      |
| jellyfin-movies       | Movie media files        |
| filebrowser-config    | Config for TV FileBrowser|
| filebrowser2-config   | Config for Movie FileBrowser|

## 👤 Author
 
Created and maintained by [Me](https://github.com/jonathan-priebe)
📫 Reach me via GitHub or [LinkedIn](https://www.linkedin.com/in/jonathan-priebe25) 
