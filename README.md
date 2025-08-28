
---

## Kurulum & Çalıştırma
> Gereksinimler: **Node 18+**, **pnpm**, (opsiyonel) **Docker**, **cloudflared**

```bash
# 1) Bağımlılıklar
pnpm -v || npm i -g pnpm
pnpm install

# 2) Env (örnek)
# client/.env.local
# NEXT_PUBLIC_SOCKET_URL=http://localhost:4000
# server/.env
# PORT=4000
# DATABASE_URL=file:./dev.db

# 3) Geliştirme
cd client && pnpm dev           # http://localhost:3000
cd ../server && pnpm dev        # ws://localhost:4000

# 4) Git (ilk push)
git init && git add .
git commit -m "feat: StarBox alpha skeleton"
git branch -M main
git remote add origin <REPO_URL>
git push -u origin main
