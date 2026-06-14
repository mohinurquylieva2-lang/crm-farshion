# EduCRM Pro — Ta'lim Markazi Boshqaruv Tizimi

O'quv markazlar uchun zamonaviy CRM tizimi. O'quvchilar, guruhlar, o'qituvchilar, davomat, to'lovlar va hisobotlarni bitta platformada boshqaring.

## Demo kirish

| Rol | Email | Parol |
|-----|-------|-------|
| Admin | `admin@educrm.uz` | `Admin1234!` |
| O'qituvchi | `teacher@educrm.uz` | `Teacher1234!` |

---

## Imkoniyatlar

- **Dashboard** — KPI kartalar, daromad grafigi, guruh to'ldirilishi, qarzdorlar
- **O'quvchilar** — CRUD, holat filtri, guruh bo'yicha filtrlash, batafsil ko'rish
- **Guruhlar** — CRUD, fan/daraja/o'qituvchi, o'quvchilar soni
- **O'qituvchilar** — CRUD, fan, maosh (belgilangan / foizli)
- **Davomat** — Guruh va sana bo'yicha olish, tarix ko'rish
- **To'lovlar** — To'lov qabul qilish, qarzdorlar ro'yxati, filtrlash
- **Vazifalar** — Homework / test / imtihon / loyiha, natijalar
- **Hisobotlar** — Grafiklar, o'qituvchilar samaradorligi, fanlar taqsimoti
- **Sozlamalar** — Markaz ma'lumotlari, ish rejimi, bildirishnomalar, obuna

## Texnologiyalar

### Frontend
- **React 18** + **TypeScript**
- **Tailwind CSS v4** — styling
- **Recharts** — grafiklar va diagrammalar
- **Lucide React** — ikonalar
- **React Hook Form** — form validatsiyasi
- **Vite** — build tool

### Backend
- **FastAPI** — REST API
- **PostgreSQL** — ma'lumotlar bazasi
- **SQLAlchemy** + **Alembic** — ORM va migratsiyalar
- **Docker / Docker Compose** — konteynerlashtirish
- **Nginx** — reverse proxy
- **Terraform** — infratuzilma (DigitalOcean)

## Ishga tushirish

### Frontend (lokal)

```bash
cd Frontend
npm install
npm run dev
```

Brauzerda `http://localhost:5173` manzilini oching.

### Backend (Docker bilan)

```bash
cd Backend
cp .env.example .env
# .env faylni to'ldiring
docker-compose up -d
```

API `http://localhost:8000` manzilida ishlaydi.  
Swagger docs: `http://localhost:8000/docs`

### Backend (lokal, Docker'siz)

```bash
cd Backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
alembic upgrade head
uvicorn app.main:app --reload
```

## Responsive dizayn

| Qurilma | Kenglik | Holati |
|---------|---------|--------|
| Telefon | < 640px | Drawer sidebar, 1-2 kolonnali grid |
| Planshet | 640–1024px | Drawer sidebar, 2 kolonnali grid |
| Kompyuter | > 1024px | Doimiy sidebar (kengaytiriladi/qisqaradi) |

## Loyiha tuzilmasi

```
EduCRM/
├── Frontend/
│   ├── guidelines/src/
│   │   ├── app/
│   │   │   ├── components/     # Barcha UI komponentlar
│   │   │   │   ├── auth/       # Login / Ro'yxatdan o'tish
│   │   │   │   └── ui/         # shadcn/ui komponentlari
│   │   │   ├── context/        # AuthContext
│   │   │   ├── data/           # Mock ma'lumotlar
│   │   │   └── types.ts        # TypeScript turlari
│   │   └── styles/             # CSS fayllar
│   ├── index.html
│   ├── vite.config.ts
│   └── package.json
│
└── Backend/
    ├── app/
    │   ├── models/             # SQLAlchemy modellari
    │   ├── routers/            # API yo'nalishlari
    │   ├── schemas/            # Pydantic schemalari
    │   └── services/           # Biznes mantiq
    ├── alembic/                # Ma'lumotlar bazasi migratsiyalari
    ├── tests/                  # Pytest testlar
    ├── nginx/                  # Nginx konfiguratsiyasi
    ├── terraform/              # Infratuzilma kodi
    └── docker-compose.yml
```

## Muhit o'zgaruvchilari

`Backend/.env.example` faylini nusxa ko'chirib `.env` nomini bering va quyidagi qiymatlarni to'ldiring:

```env
DATABASE_URL=postgresql://user:password@localhost:5432/educrm
SECRET_KEY=your-secret-key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

## Testlar

```bash
cd Backend
pytest tests/ -v
```

## Litsenziya

MIT License © 2026 EduCRM Pro
