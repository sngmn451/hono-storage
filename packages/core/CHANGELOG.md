# @hono-storage/core

## 0.0.14

### Patch Changes

- [#71](https://github.com/sor4chi/hono-storage/pull/71) [`1649e17`](https://github.com/sor4chi/hono-storage/commit/1649e172335fd7780f04412f72769ab7d991a790) Thanks [@sngmn451](https://github.com/sngmn451)! - feat: preserve File type property in HonoStorageFile
  When a File is processed by the storage middleware, the `type` property from the original File object is now correctly inherited by HonoStorageFile. This ensures the file's content-type is maintained during file uploads.

## 0.0.13

### Patch Changes

- [#65](https://github.com/sor4chi/hono-storage/pull/65) [`474a669`](https://github.com/sor4chi/hono-storage/commit/474a669a8f43156aafa58173390504d355ff1b7f) Thanks [@sor4chi](https://github.com/sor4chi)! - fix: remove `File` (`@web-std/file`) polyfill from `@hono-storage/core` package

  This changes means that **stop Node.js v18 support** for `@hono-storage/core` package.

  `@web-std/file` is a polyfill for the `File` class, but for web compatibility, it's not necessary to adapt the `File` class to Node.js.
  So if you want to Hono Storage to work on older Node.js versions, you can use the `@web-std/file` package manually.

## 0.0.12

### Patch Changes

- [#52](https://github.com/sor4chi/hono-storage/pull/52) [`41803f8`](https://github.com/sor4chi/hono-storage/commit/41803f8dbb3ec30ff03720e510e01563b7153b5b) Thanks [@sor4chi](https://github.com/sor4chi)! - Add require exports field for cjs usecase

## 0.0.11

### Patch Changes

- [#51](https://github.com/sor4chi/hono-storage/pull/51) [`301f6e9`](https://github.com/sor4chi/hono-storage/commit/301f6e9b2e6762b350fc0b3c1316e109fc843917) Thanks [@sor4chi](https://github.com/sor4chi)! - Move Hono to peerDependencies. Hono Storage now has compatibility with Hono v3.8 or later.

## 0.0.10

### Patch Changes

- [#47](https://github.com/sor4chi/hono-storage/pull/47) [`0cc024e`](https://github.com/sor4chi/hono-storage/commit/0cc024eb7dc065bb648f34c52174b0b1baa8d044) Thanks [@sor4chi](https://github.com/sor4chi)! - update Hono's version to v4.3.2

## 0.0.9

### Patch Changes

- [`628e0dc`](https://github.com/sor4chi/hono-storage/commit/628e0dcd6b48953db1d212e317c1d470499780e3) Thanks [@sor4chi](https://github.com/sor4chi)! - fix package.json

## 0.0.8

### Patch Changes

- [#38](https://github.com/sor4chi/hono-storage/pull/38) [`0fffc7f`](https://github.com/sor4chi/hono-storage/commit/0fffc7f76152df882b15398014ca8aa331a6ff12) Thanks [@sor4chi](https://github.com/sor4chi)! - feat: add `field` property to `HonoStorageFile`(HSF).

## 0.0.7

### Patch Changes

- [#36](https://github.com/sor4chi/hono-storage/pull/36) [`17d6090`](https://github.com/sor4chi/hono-storage/commit/17d609093ade861c93eaac5418ca0a7debb7bebb) Thanks [@sor4chi](https://github.com/sor4chi)! - Fix: collectly handle storage when one file posted to multiple middleware

- [`0d257d4`](https://github.com/sor4chi/hono-storage/commit/0d257d42f158bc4485e907d601a6541d0f25a923) Thanks [@sor4chi](https://github.com/sor4chi)! - Breaking Changes: change the way to define multiple middleware option for scalability

  ```ts
  // Before
  storage.multiple("field", 3); // max 3 files options

  // After
  storage.multiple("filed", { maxCount: 3 }); // max 3 files options
  ```

## 0.0.6

### Patch Changes

- [#33](https://github.com/sor4chi/hono-storage/pull/33) [`acf1f0d`](https://github.com/sor4chi/hono-storage/commit/acf1f0de6d1c88224182ead9aff3578c5c8842d4) Thanks [@sor4chi](https://github.com/sor4chi)! - `c.var.files` became type-safe

  ```ts
  app.post("/single", storage.single("image"), (c) => {
    const image = c.var.files.image; // string | File | undefined
  });

  app.post("/multiple", storage.multiple("images"), (c) => {
    const images = c.var.files.images; // (string | File)[]
  });
  ```

- [#30](https://github.com/sor4chi/hono-storage/pull/30) [`6da696f`](https://github.com/sor4chi/hono-storage/commit/6da696f952a6bfeac95725bd077deebba9da8591) Thanks [@sor4chi](https://github.com/sor4chi)! - Breaking Change: Rename `storage.array` to `storage.multiple`.

## 0.0.5

### Patch Changes

- [#28](https://github.com/sor4chi/hono-storage/pull/28) [`51fa375`](https://github.com/sor4chi/hono-storage/commit/51fa3752a49ddb7403edb57b0f1a1feaf154978b) Thanks [@sor4chi](https://github.com/sor4chi)! - Breaking change: The argument of `storage.field` function is changed.

  ## Before

  ```ts
  storage.field([{ name: "files", maxCount: 3 }, { name: "image" }]);
  ```

  ## After

  ```ts
  storage.field({
    files: { type: "multiple", maxCount: 3 },
    image: { type: "single" },
  });
  ```

## 0.0.4

### Patch Changes

- [#24](https://github.com/sor4chi/hono-storage/pull/24) [`07d2d99`](https://github.com/sor4chi/hono-storage/commit/07d2d99cdf20a1694cc03c965da773754ad6fa61) Thanks [@sor4chi](https://github.com/sor4chi)! - ## `storage.field` performance improvement

  `storage.field` is able to upload each fields in parallel now.

## 0.0.3

### Patch Changes

- [`f03e4a4`](https://github.com/sor4chi/hono-storage/commit/f03e4a41d705fa8883cef1dce85784825ea05eae) Thanks [@sor4chi](https://github.com/sor4chi)! - Update hono version to 3.8.1

## 0.0.2

### Patch Changes

- [#7](https://github.com/sor4chi/hono-storage/pull/7) [`ea1eb7a`](https://github.com/sor4chi/hono-storage/commit/ea1eb7a533b8ba3d08acc80f92b8153a9048bfc9) Thanks [@sor4chi](https://github.com/sor4chi)! - file helper for HonoStorage

  ```ts
  import { HonoStorageFile } from "@hono-storage/core";

  const file = new File([blob], "filename.ext.zip");
  const HSfile = new HonoStorageFile(file);
  HSfile.originalname; // => name part of file (filename.ext)
  HSfile.extensiton; // => extension part of file (.zip)
  ```

## 0.0.1

### Patch Changes

- [`a7ade7f`](https://github.com/sor4chi/hono-storage/commit/a7ade7f3bb67cbf3b70efbdf91e9260043413f16) Thanks [@sor4chi](https://github.com/sor4chi)! - This is Hono Storage, a simple and easy to use file storage library.

  ```bash
  npm install @hono-storage/core
  ```

  ```ts
  import { HonoStorage } from "@hono-storage/core";
  import { Hono } from "hono";

  const app = new Hono();
  const storage = new HonoStorage({
    storage: (c, files) => {
      // do something with the files, eg, upload to s3, or save to local, etc.
    },
  });

  app.post("/upload/single", storage.single("image"), (c) => c.text("OK"));
  app.post("/upload/array", storage.array("pictures"), (c) => c.text("OK"));
  app.post(
    "/upload/field",
    storage.fields([
      { name: "image", maxCount: 1 },
      { name: "pictures", maxCount: 2 },
    ]),
    (c) => c.text("OK"),
  );

  // and you can get parsed formData easily
  app.post("/upload/vars", storage.single("image"), (c) => {
    const { image } = c.get("files");
    // do something with file
    return c.text("OK");
  });
  ```
