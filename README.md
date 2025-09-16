# AI Business Dashboard (monorepo)

## Setup

1. Install dependencies

```bash
npm install
```

2. Start both dev servers

```bash
npm run dev
# or individually:
npm run dev:frontend
npm run dev:backend
```

3. Run with Docker Compose (integration/demo)

```bash
docker-compose up --build
```

4. prisma (backed)

```bash
cd backend
npx prisma generate
npx prisma db push
```
