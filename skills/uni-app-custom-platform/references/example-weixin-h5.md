---
name: uni-app-custom-example-weixin-h5
description: Custom h5-weixin platform example based on h5
---

# Example: WeChat Service Account

A custom WeChat service account platform (`H5-WEIXIN`) extended from the `h5` base platform.

## package.json Config

```json
{
  "uni-app": {
    "scripts": {
      "h5-weixin": {
        "title": "微信服务号",
        "browser": "chrome",
        "env": {
          "UNI_PLATFORM": "h5"
        },
        "define": {
          "H5-WEIXIN": true
        }
      }
    }
  }
}
```

## Use Custom Platform in Code

```javascript
// #ifdef H5
H5平台通用代码（含微信服务号）
// #endif

// #ifdef H5-WEIXIN
微信服务号特有代码
// #endif
```

## Run and Publish

```bash
npm run dev:custom h5-weixin
npm run build:custom h5-weixin
```

In HBuilderX, the Run/Release menu shows a "微信服务号" item — click it to compile.

## Output and Preview

The compilation output is in the `h5` directory. Since `browser` is set to `chrome`, the compiled web output targets Chrome. Open the output in Chrome to preview the WeChat service account site.

## Use Case

This is useful when you need one codebase compiled to different deployed websites — e.g. a main site and a WeChat H5 site — with truly separated deployment (not responsive adaptation within one site).
