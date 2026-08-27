---
name: uni-app-custom-config-structure
description: package.json uni-app.scripts extension node fields and structure
---

# Config Structure

Custom platforms are defined by adding a `uni-app` extension node to `package.json`. The node contains a `scripts` object, where each key is a custom platform name and the value is its configuration.

## Full Config Template

```json
{
  "uni-app": {
    "scripts": {
      "custom-platform": {
        "title": "自定义扩展名称",
        "browser": "",
        "env": {
          "UNI_PLATFORM": "",
          "MY_TEST": ""
        },
        "define": {
          "CUSTOM-CONST": true
        }
      }
    }
  }
}
```

## Field Reference

| Field | Type | Required | Description |
|------|------|----------|-------------|
| `title` | string | Yes | Display name shown in HBuilderX Run/Release menu |
| `browser` | string | No | Target browser, only effective when `UNI_PLATFORM` is `h5` |
| `env` | object | Yes | Environment variables for the custom platform |
| `env.UNI_PLATFORM` | string | Yes | Base platform enum value (e.g. `h5`, `mp-alipay`) |
| `env.*` | string | No | Other custom environment variables |
| `define` | object | Yes | Custom condition compilation constants |
| `define.*` | boolean | Yes | Custom condition compilation constant, **recommended uppercase** |

## Important Notes

- `package.json` **does not allow comments** — JSON with comments makes the extension config invalid
- `UNI_PLATFORM` only accepts the supported base platform enum values
- `define` constants should be uppercase (e.g. `MP-DINGTALK`, `H5-WEIXIN`)
- `browser` only takes effect when `UNI_PLATFORM` is `h5`

## Accessing env in Code

| Vue Version | Access Path |
|------------|-------------|
| vue2 | `process.UNI_SCRIPT_ENV` |
| vue3 | `process.env.UNI_CUSTOM_DEFINE` |

## Tooling Requirements

- vue-cli: latest version
- HBuilderX: 2.1.6+
