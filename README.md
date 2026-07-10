# Santos Reparación de Llantas — Web PMV

Landing page de alta conversión para taller de reparación de llantas en Chillán, Chile.

## Stack

- **Next.js 14** (App Router + React Server Components)
- **TailwindCSS 3** con tokens de color custom
- **Framer Motion** (disponible para animaciones adicionales)
- **react-dropzone** (subida de fotos en el wizard)

## Inicio rápido

```bash
npm install
npm run dev     # http://localhost:3000
npm run build   # build de producción
```

## Estructura del proyecto

```
src/
├── app/
│   ├── layout.tsx          # Root layout + SEO global + Schema.org
│   └── page.tsx            # Página principal (8 secciones)
├── components/sections/
│   ├── HeroSection.tsx     # Hero con contador animado
│   ├── RepairWizard.tsx    # App evaluación (4 pasos)
│   ├── BeforeAfterSlider.tsx
│   ├── ServicesSection.tsx  # SEO-optimizada
│   ├── HowWeWork.tsx
│   ├── Testimonials.tsx
│   ├── FAQ.tsx             # Accordion SEO
│   └── Footer.tsx          # Mapa + WhatsApp flotante
└── lib/
    ├── repairability.ts    # Reglas de negocio (puras, testables)
    └── seo.ts              # Metadata + Schema.org LocalBusiness
```

## Lógica de reparabilidad

Las reglas viven en `src/lib/repairability.ts` y son fácilmente portables a Python:

| Condición | Resultado |
|-----------|-----------|
| Abolladura/fisura/pérdida en **pestaña** | Reparable ✓ |
| Daño **cerca de los rayos** | No reparable ✗ |
| **3+ daños** acumulados | No recomendable ✗ |

## SEO

- Schema.org `AutoRepair` con geo, horarios y servicios
- Keywords: "reparación de llantas Chillán", "torno llantas", "soldadura llantas"
- Open Graph configurado
- Sitemap listo para agregar

## Configurar información del negocio

Edita `src/lib/seo.ts`:

```typescript
export const siteConfig = {
  phone: "+56962372869",
  whatsapp: "56962372869",
  address: "Condell 33, Chillán",
  lat: -36.6063,
  lng: -72.1034,
  instagram: "https://instagram.com/...",
  facebook: "https://facebook.com/...",
};
```

## Deploy

### Vercel (recomendado)
```bash
npx vercel --prod
```

### Servidor propio
```bash
npm run build
npm start
```

## Próximos pasos (post-PMV)

- [ ] Integrar Claude Vision API en `/api/evaluate/route.ts` para análisis de imagen real
- [ ] Galería real de antes/después con imágenes del taller
- [ ] Google Business Profile integration
- [ ] Google Analytics + Search Console
- [ ] Blog de contenido SEO (cuidado de llantas, etc.)
