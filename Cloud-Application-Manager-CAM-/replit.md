Intelligent Cloud Application Catalog System
Overview
pnpm workspace monorepo using TypeScript. Full-stack cloud application catalog system with React frontend and Express backend.

Stack
Monorepo tool: pnpm workspaces
Node.js version: 24
Package manager: pnpm
TypeScript version: 5.9
API framework: Express 5
Database: PostgreSQL + Drizzle ORM
Validation: Zod (zod/v4), drizzle-zod
API codegen: Orval (from OpenAPI spec)
Build: esbuild (CJS bundle)
Frontend: React + Vite + Tailwind CSS
Charts: Recharts
Routing: Wouter
Auth: Mock auth (admin/password)
Features
Dashboard: Total apps, categories, usage stats, category pie chart, most-used bar chart
Application List: Search, filter by category, sort, pagination
Add/Edit Application: Full form with versions, tags, dependencies
Application Details: Version history, dependencies, usage stats, recommendations
Analytics: Category distribution, tag cloud, usage ranking, top 5 most-used
Recommendations: Intelligent recommendations based on category, tags, usage
Dark Mode: Toggle stored in localStorage
Toast Notifications: Via Sonner
Key Commands
pnpm run typecheck — full typecheck across all packages
pnpm run build — typecheck + build all packages
pnpm --filter @workspace/api-spec run codegen — regenerate API hooks and Zod schemas from OpenAPI spec
pnpm --filter @workspace/db run push — push DB schema changes (dev only)
pnpm --filter @workspace/api-server run dev — run API server locally
API Endpoints
POST /api/login — mock auth (admin/password)
GET/POST /api/applications — list/create apps
GET/PUT/DELETE /api/applications/:id — get/update/delete app
POST /api/applications/:id/increment-usage — increment usage
GET /api/analytics/most-used — top N most used
GET /api/analytics/category-distribution — count per category
GET /api/analytics/dashboard-summary — summary stats
GET /api/analytics/tag-distribution — tag usage counts
GET /api/recommendations/:id — intelligent recommendations
Database Schema
applications table:

id (serial PK)
name, description (text)
versions (text[])
category (text)
tags (text[])
usage_count (integer)
dependency_ids (integer[])
created_at, updated_at (timestamptz)
Architecture
artifacts/cloud-catalog/ — React/Vite frontend
artifacts/api-server/ — Express API server
lib/db/ — Drizzle ORM + PostgreSQL schema
lib/api-spec/openapi.yaml — OpenAPI contract
lib/api-client-react/ — Generated React Query hooks
lib/api-zod/ — Generated Zod schemas
See the pnpm-workspace skill for workspace structure, TypeScript setup, and package details.
