---
name: uni-app-custom-example-dingtalk
description: Custom mp-dingtalk platform example based on mp-alipay
---

# Example: DingTalk Mini Program

A custom DingTalk mini-program (`MP-DINGTALK`) extended from the Alipay mini-program base platform.

## package.json Config

```json
{
  "uni-app": {
    "scripts": {
      "mp-dingtalk": {
        "title": "钉钉小程序",
        "env": {
          "UNI_PLATFORM": "mp-alipay"
        },
        "define": {
          "MP-DINGTALK": true
        }
      }
    }
  }
}
```

## Use Custom Platform in Code

```javascript
// #ifdef MP
小程序平台通用代码（含钉钉）
// #endif

// #ifdef MP-ALIPAY
支付宝平台通用代码（含钉钉）
// #endif

// #ifdef MP-DINGTALK
钉钉平台特有代码
// #endif
```

## Run and Publish

```bash
npm run dev:custom mp-dingtalk
npm run build:custom mp-dingtalk
```

In HBuilderX, the Run/Release menu shows a "钉钉小程序" item — click it to compile.

## Output and Preview

The compilation output is still in the `mp-alipay` directory. To preview and publish:

1. Open Alipay Developer Tools
2. Select "钉钉小程序" (DingTalk Mini Program) as the project type
3. Open the `mp-alipay` output directory
4. Preview and publish via the DingTalk workflow
