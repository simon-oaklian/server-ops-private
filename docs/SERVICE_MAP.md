# Service Map

Last reviewed: 2026-05-22

## Cloudflare Tunnel Routing

Routes observed in Cloudflare tunnel config, redacted to hostnames and local services only:

| Hostname | Local Service |
|---|---|
| openclaw.oaklian.com | http://localhost:8090 |
| i.oaklian.com | http://localhost:5678 |
| crm.oaklian.com | http://localhost:8069 |
| oaklian.com | http://localhost:8080 |
| www.oaklian.com | http://localhost:8080 |
| jnono.com | http://localhost:8000 |
| www.jnono.com | http://localhost:8000 |
| pricvo.com | http://localhost:3017 |
| www.pricvo.com | http://localhost:3017 |
| jzozo.com | http://localhost:3100 |
| www.jzozo.com | http://localhost:3100 |

Fallback route: http_status:404.

## Host Nginx

Active host-level Nginx site files observed:

- /etc/nginx/sites-enabled/jnono -> /etc/nginx/sites-available/jnono
- /etc/nginx/sites-enabled/openclaw -> /etc/nginx/sites-available/openclaw

Nginx config files may include production routing. Do not copy raw configs to GitHub until secrets and private hostnames are reviewed.

## Oaklian Publishing Relationship

Observed relationship:

- Production Oaklian app lives at /var/www/oaklian, served by oaklian.service on port 4174.
- SEO V4 project lives at /home/simon/AI-SEO-oaklian.
- SEO V4 Docker generator bind-mounts /var/www/oaklian as /oaklian with write access.
- SEO V4 static web container serves /home/simon/AI-SEO-oaklian/site on port 8080.
- Cloudflare currently points oaklian.com to localhost:8080.

Operational caution: before changing Oaklian or SEO V4, confirm whether the route being fixed is served from /var/www/oaklian, /home/simon/AI-SEO-oaklian/site, or both.

## Known 2026-05-22 SEO Fix

Fixed high-traffic 404:

- Restored /en/insights/what-bad-shower-waterproofing-looks-like-under-floor/
- Source content copied from /en/insights/bad-shower-waterproofing-damage-bay-area/
- Canonical, Open Graph URL, and schema URL updated to the restored URL
- Added restored URL to sitemap.xml and sitemap-new.xml
- Verified public 200 response

Backup created before fix:

- /home/simon/oaklian_restore_old_slug_20260522_0918/
- /var/www/oaklian/sitemap.xml.bak_restore_old_slug_20260522_0918
- /var/www/oaklian/sitemap-new.xml.bak_restore_old_slug_20260522_0918
