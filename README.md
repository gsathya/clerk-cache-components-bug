Repro for Clerk and cache components in nextjs bug

## Getting Started

First, run the development server:

```bash
$ pnpm i
$ pnpm dev
```

Open [http://localhost:3000/test/1](http://localhost:3000/test/1) with your browser to see this error:

```bash
 GET / 404 in 2.6s (compile: 1043ms, proxy.ts: 1417ms, render: 145ms)
Error: Route "/test/[kind]": Uncached data was accessed outside of <Suspense>. This delays the entire page from rendering, resulting in a slow user experience. Learn more: https://nextjs.org/docs/messages/blocking-route
    at RootLayout (app/layout.tsx:35:5)
  33 | }>) {
  34 |   return (
> 35 |     <ClerkProvider>
     |     ^
  36 |       <html lang="en">
  37 |         <body
  38 |           className={`${geistSans.variable} ${geistMono.variable} antialiased`}
```

## Insights

The error only happens in routes with dynamic segments. If you remove the [[kind]] route segment, the error goes away.