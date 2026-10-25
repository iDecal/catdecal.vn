# CatDecal v2.9 — Hướng dẫn triển khai

Dự án này là Astro static, build ra `dist/`, phù hợp Cloudflare Pages.

## Nếu dùng Cloudflare Pages Git integration
- Build command: `npm run build`
- Output directory: `dist`
- Root: `/`
- Pages sẽ tự publish; không cần lệnh deploy riêng.

## Nếu dùng pipeline yêu cầu Deploy command
- Build command: `npm run build`
- Deploy command: `npx wrangler pages deploy dist --project-name=catdecalvn`
- API token phải có Account > Cloudflare Pages > Edit cho đúng account.
- Nếu có `CLOUDFLARE_API_TOKEN` cũ, cập nhật bằng token hợp lệ.
- `Authentication error [code: 10000]` không thể sửa bằng code Astro.

## Lưu ý
- `worker/index.js` là mã Worker riêng, không tự chạy khi deploy Pages.
- `functions/api/bao-gia.js` là Pages Function; nếu cần R2, phải cấu hình binding tương ứng trong Pages.
- Không thêm `main` hay `assets` vào wrangler.json để chữa lỗi API Token.
