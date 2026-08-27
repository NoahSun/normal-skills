---
name: uni-app-custom-base-platforms
description: Supported UNI_PLATFORM enum values and browser values for custom platform extension
---

# Base Platforms

Custom platforms in uni-app are extended **on top of** a base platform. The base platform is specified via the `UNI_PLATFORM` environment variable in `package.json`'s `uni-app.scripts.<name>.env`.

## Supported `UNI_PLATFORM` Values

`UNI_PLATFORM` only accepts the following enum values — these are the base platforms uni-app natively supports:

| Value | Base Platform |
|-------|---------------|
| `h5` | Web / H5 |
| `mp-weixin` | WeChat Mini Program |
| `mp-alipay` | Alipay Mini Program |
| `mp-baidu` | Baidu Smart Program |
| `mp-toutiao` | Douyin Mini Program |
| `mp-qq` | QQ Mini Program |

## Supported `browser` Values

The `browser` field is **only effective when `UNI_PLATFORM` is `h5`**. It controls the target browser for the compiled web output.

| Value | Browser |
|-------|---------|
| `chrome` | Google Chrome |
| `firefox` | Mozilla Firefox |
| `ie` | Internet Explorer |
| `edge` | Microsoft Edge |
| `safari` | Apple Safari |
| `hbuilderx` | HBuilderX built-in browser |

## Constraints

- Only web and mini-program platforms can be extended, **not** app packaging
- Mini-program extensions must be based on a specified base platform (sub-platform only)
- The base platform itself cannot be extended
