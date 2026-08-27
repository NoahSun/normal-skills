---
name: uni-app-custom-platform
description: uni-app 自定义平台扩展。Use when extending uni-app with custom compilation platforms (e.g. DingTalk mini-program, WeChat service account H5) via package.json uni-app.scripts, defining custom condition compilation constants, and running/building custom platforms.
metadata:
  author: NoahSun
  version: "2026.8.27"
  source: Generated from https://uniapp.dcloud.net.cn/collocation/package.html
---

# uni-app Custom Platform

> The skill is based on uni-app custom platform documentation, generated at 2026-08-27.

uni-app allows extending custom condition compilation platforms by adding a `uni-app` extension node in `package.json`. This enables one codebase to compile and deploy to different sites (e.g. main site vs WeChat H5) or to extend mini-program platforms (e.g. DingTalk/Taobao based on Alipay mini-program).

After extending a new platform, it has 3 effects:
1. Custom condition compilation code can be written for the new platform
2. Compilation can be executed for the new platform at runtime
3. Compilation and distribution can be executed for the new platform on release

**Important constraints:**
- Only web and mini-program platforms can be extended, **not** app packaging
- Mini-program extensions must be based on a specified base platform (sub-platform only), the base platform itself cannot be extended

## Core References

| Topic | Description | Reference |
|-------|-------------|-----------|
| Base Platforms | Supported `UNI_PLATFORM` enum values and `browser` values | [base-platforms](references/base-platforms.md) |
| Config Structure | `package.json` `uni-app.scripts` extension node fields | [config-structure](references/config-structure.md) |

## Usage

| Topic | Description | Reference |
|-------|-------------|-----------|
| Condition Compilation | Use custom constants in code via `#ifdef` / `#ifndef` | [condition-compilation](references/condition-compilation.md) |
| CLI Commands | Run and build custom platforms via `npm run dev:custom` | [cli-commands](references/cli-commands.md) |

## Examples

| Topic | Description | Reference |
|-------|-------------|-----------|
| DingTalk Mini Program | Custom `mp-dingtalk` based on `mp-alipay` | [example-dingtalk](references/example-dingtalk.md) |
| WeChat Service Account | Custom `h5-weixin` based on `h5` | [example-weixin-h5](references/example-weixin-h5.md) |

## Key Recommendations

- **No comments in `package.json`** — JSON does not allow comments, otherwise the extension config is invalid
- **Use uppercase for `define` constants** — e.g. `MP-DINGTALK`, `H5-WEIXIN`
- **Base platform must be a supported enum** — `UNI_PLATFORM` only accepts `h5`, `mp-weixin`, `mp-alipay`, `mp-baidu`, `mp-toutiao`, `mp-qq`
- **`browser` only works when `UNI_PLATFORM` is `h5`** — accepts `chrome`, `firefox`, `ie`, `edge`, `safari`, `hbuilderx`
- **Keep tooling up to date** — vue-cli latest, HBuilderX 2.1.6+
- **Access env in code** — vue2: `process.UNI_SCRIPT_ENV`; vue3: `process.env.UNI_CUSTOM_DEFINE`
