# StarBox · Web Tabanlı Online Oyun (Alfa v0.1)

Uzay kaşifleri olarak **simsiyah yıldız boşluğunda** kare gezegenlere **warp** at, **kaynak topla** (Metal/Ahşap), **yapı kur**, **kuleleri fethet** ve final hedef **Kuroi** gezegeninin kulesine **bayrak** dik. Maç bazlı (20–25 dk), **2–4 oyuncu**, FFA.

> **Host modeli:** Oyun sunucusu **senin PC’inde** çalışır (otoriter sunucu). İnternete açmak için **Cloudflare Tunnel + Access** kullanılır.

---

## İçindekiler
- [Özellikler](#özellikler)
- [Oynanış Akışı](#oynanış-akışı)
- [Maç Kuralları](#maç-kuralları)
- [Gezegenler & Eşikler](#gezegenler--eşikler)
- [Kaynaklar & Ekonomi](#kaynaklar--ekonomi)
- [İlerleme (Craft + Perk)](#ilerleme-craft--perk)
- [Yapılar (Limitler)](#yapılar-limitler)
- [Warp & Hareketlilik](#warp--hareketlilik)
- [HUD & Bildirimler](#hud--bildirimler)
- [Teknoloji & Mimari](#teknoloji--mimari)
- [Klasör Düzeni](#klasör-düzeni)
- [Kurulum & Çalıştırma](#kurulum--çalıştırma)
- [Cloudflare Yayın (Host PC)](#cloudflare-yayın-host-pc)
- [Anti-Cheat & Güvenlik](#anti-cheat--güvenlik)
- [Telemetri & Loglama](#telemetri--loglama)
- [Yol Haritası](#yol-haritası)
- [Lisans](#lisans)

---

## Özellikler
- **Maç Bazlı:** 20–25 dk hedef, **2–4 oyuncu**, FFA.
- **Gezegen Atlama:** 4 Kolay + 3 Orta + 2 Zor + **1 Final (Kuroi)**.
- **Ekonomi:** Coin (gelir), Metal & Ahşap (craft/inşa).
- **Savaş:** Kule HP düşür → **fethet** → **kilit** süresi başlar.
- **İlerleme:** **Craft** (kıyafet/teçhizat kapıları) + **Perk** (seviye).
- **Host PC:** Otoriter sunucu; Cloudflare Tunnel üzerinden internet.

---

## Oynanış Akışı
1. **Lobi:** Parolalı oda; 2+ oyuncu → geri sayım (60 sn). 4 oyuncuysa 20 sn.
2. **Galaksi:** Yıldız boşluğu + kare gezegenler; seç ve **warp**.
3. **Gezegen:** Kaynak topla (elle kazı + sondalar), **yapı kur**, **craft** yap.
4. **Savaş:** Kulelere saldır, sahip ol; bildirimlerden savunmaya koş.
5. **Final:** **Kuroi** kulesini ilk alan **kazanır** (erken bitiş). Süre biterse skorlamayla zafer.

---

## Maç Kuralları
- **Süre:** 20–25 dk (Kuroi düşerse **erken bitiş**).
- **Oyuncu:** **2–4** (herkes tek).
- **Zafer (tie-break):** ① kule geliri toplamı ② fethedilen kule sayısı ③ coin.
- **DPS tavanı:** oyuncu başı **18**, kule başına **60** (toplam).
- **Kule HP:** Kolay **600**, Orta **900**, Zor **1300**, **Kuroi 2200**  
  _(2–4 oyuncuya göre dinamik ölçek çarpanı ile süre hedefi korunur)_
- **Regen:** saldırı yoksa **5 sn** sonra **+6 HP/sn**.
- **Fetih kilidi:** **90 sn** (o kuleye karşı saldırı kapalı).
- **Geç katılım:** Maç başladıktan **ilk 3 dk** açık.
- **AFK/Leaver:** 60 sn uyarı → 90 sn “**gölge mod**” (gelir %50, saldırı yok). Kopan oyuncu **2 dk** içinde dönerse durum korunur.

---

## Gezegenler & Eşikler
| Tip | Rol/Örnek | Giriş Eşikleri | Kaynak Çarpanları (ör.) |
| --- | --- | --- | --- |
| **Kolay (×4)** | Verdant (orman) | Helmet L1, Suit L1 | Metal ×0.9–1.2, Ahşap ×1.0–1.5 |
| **Orta (×3)** | Astra (buz) | Helmet L2 **veya** Shield L1 | Metal ×1.2–1.6, Ahşap ×0.6–1.2 |
| **Zor (×2)** | Ferrum (çöl) | Suit L2 + Shield L1 | Metal ×1.6–2.0, Ahşap ×0.4–0.9 |
| **Final (×1)** | **Kuroi** (volkanik-gece) | Helmet L2 + Suit L2 + Shield L2 | Metal ×1.7, Ahşap ×0.1 |

> **Not:** Eşikleri karşılamayan ekipman ile warp yapılamaz (UI kırmızı uyarı verir).

---

## Kaynaklar & Ekonomi
- **Başlangıç:** 300c; **Helmet L1 + Suit L1**
- **Elle Kazı:** her **3 sn** → **+2~4 Metal**, **+1~3 Ahşap** _(gezegen çarpanı uygulanır)_
- **Kule Geliri (coin/dk):** Kolay **+20**, Orta **+35**, Zor **+50**, **Kuroi +90**
- **Catch-up:** Son 3 dk’da kule geliri **0** olan oyuncuya **+15c/dk** taban gelir.  
  Son 2 dk **kulesiz** oyuncuya **Zor warp maliyeti 5c**.

---

## İlerleme (Craft + Perk)
- **Craft (kıyafet):**  
  - Helmet **L2** → **150M + 80A + 250c**  
  - Suit **L2** → **220M + 120A + 350c**  
  - Shield **L1/L2** → **160M+100A+300c / 300M+160A+500c**
- **Perk’ler (level ile):**  
  - **Miner I/II**: kazı verimi +%10/+%20  
  - **Coolant**: overheat eşiği +%15  
  - **Logistics**: warp cd −%20  
  - **Fortify**: fetih kilidi +15 sn

---

## Yapılar (Limitler)
Gezegen başına **oyuncu limiti**:
- **Maden Sondası I** — `120M + 60A` → **+6 Metal/dk** _(max **2**)_
- **Depo I** — `80M + 80A` → **+200 kapasite** _(max **1**)_
- **Atölye I** — `200M + 120A` → **craft** açılır _(max **1**)_
- **Savunma Tareti I** — `220M + 60A` → kule savunmasına destek _(max **1**, kule tavanına **dahil değil**)_  
> Yapılar **ele geçirilemez**, fakat **Zor/Kuroi**’da **imha edilebilir** (imha → %50 kaynak iadesi).

---

## Warp & Hareketlilik
- **Cooldown:** **30 sn** _(Logistics perk ile 24 sn)_
- **Maliyet:** Kolay/Orta **0c**, Zor **10c**, **Kuroi 25c**
- **Acil Warp:** Saldırı bildirim kartındaki **[Git]** → **tek kullanımlık**, cd yok sayılır.
- **Spawn Koruması:** Warp sonrası **2 sn** hasar bağışıklığı.

---

## HUD & Bildirimler
- **HUD (üst):** İsim • Seviye • Coin • Metal • Ahşap • Aktif gezegen • Ping
- **Sağ Panel Kartları:**  
  - **Saldırı:** *“Ferrum-T2 saldırı altında (00:25) [Git]”*  
  - **Gelir Özeti:** son 60 sn coin/dk  
  - **Craft Tamam:** *“Suit L2 hazır [Giy]”*  
  - **Uyarı:** *“Kuroi için Shield L2 gerekli”*

---

## Teknoloji & Mimari
- **İstemci:** **Next.js (App Router) + React + Canvas/WebGL + Zustand**
- **Sunucu:** **Node.js + Express + Socket.IO + Zod** _(otoriter)_
- **DB:** Prod **PostgreSQL**, Dev **SQLite** — **Prisma** ORM
- **Senkron:** Olay tabanlı (attack/mine/build/warp) + **tick**: savaş **10 Hz**, ekonomi **1 Hz**, üretim **3 sn**
- **Barındırma:** **Host PC** + **Cloudflare Tunnel/Access**
- **CORS/Origin:** Socket **yalnızca app alanından** bağlantı kabul eder

---

## Klasör Düzeni
```
starbox/
  client/    # Next.js (web istemci)
  server/    # Express + Socket.IO (otoriter oyun sunucusu)
  shared/    # Ortak tipler/şemalar (TS)
  docs/      # Tasarım, seed'ler, denge notları
  seed/      # Gezegen/kule/ekonomi JSON tohumları
  package.json
  pnpm-workspace.yaml
```

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
```

---

## Cloudflare Yayın (Host PC)
**Önerilen topoloji:** iki alt alan  
- `app.<alanadın>` → **client** (HTTP)  
- `socket.<alanadın>` → **server** (WS)

```bash
# Cloudflare Tunnel (örnek portlar)
# app için:
cloudflared tunnel --url http://localhost:3000
# socket için:
cloudflared tunnel --url http://localhost:4000
```

- **Access:** E-posta allowlist + OTP (Zero Trust kapısı)  
- **WS Idle timeout:** ≥ **30 dk**  
- **CORS/Origin:** Socket yalnızca `https://app.<alanadın>` kaynağını kabul eder

---

## Anti-Cheat & Güvenlik
- **Sunucu otoritesi:** hasar/kazı/craft yalnız server’da hesaplanır
- **Rate limit:** saldırı atışı **≤ 6/sn**; mine start/stop spam engeli
- **DPS tavanı:** oyuncu **18**, kule **60** toplam
- **Regen eşiği:** son 15 sn’deki max DPS’in **%25** altı → regen başlar
- **Kilitli kule:** fetih sonrası **90 sn**; bu sırada taret hasarı **%−20**
- **Log:** fetih, saldırı, kilit açılışı, AFK; JSON format

---

## Telemetri & Loglama
- **Metrikler:** `time_to_first_tower`, `avg_kuroi_attempts`, `dps_cap_hits`, `underdog_triggers`, `warp_cd_skips`
- **Hata izleme:** (opsiyonel) Sentry
- **Log dosyaları:** Maç sonu özet + olaylar disk’e yazılır

---

## Yol Haritası
- **v0.1 Alfa:** Host PC, tek maç/oda, temel ekonomi, craft+perk, bildirim/HUD, Cloudflare yayın
- **v0.2 Polish:** Miniharita, görsel/işitsel iyileştirme, geniş görev seti, kozmetik ilerleme
- **v0.3 Online+:** Redis adapter ile yatay ölçek, dereceli (MMR), sezon ödülleri, ek yapı/kule davranışları

---

## Lisans
TBD (öneri: **MIT**). Telif ve marka unsurları Tunix TGame’e aittir.

---

### Kısa İngilizce Öz (opsiyonel)
**StarBox** is a web-based, match-driven (20–25 min) 2–4 player FFA space game. Warp to square planets, mine resources (metal/wood), build structures, and capture towers. Final goal: conquer **Kuroi**. Progression combines **craft** (gear gates) + **perks**. Authoritative server (host PC) via **Cloudflare Tunnel**. Stack: Next.js + Socket.IO + Node.
