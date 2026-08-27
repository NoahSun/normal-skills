---
name: uni-app-custom-condition-compilation
description: Use custom constants in code via #ifdef / #ifndef for platform-specific code
---

# Condition Compilation

After defining a custom platform with a `define` constant in `package.json`, use uni-app's condition compilation syntax to write platform-specific code.

## Syntax

```vue
<!-- #ifdef CUSTOM-CONST -->
Code that only runs on the custom platform
<!-- #endif -->

<!-- #ifndef CUSTOM-CONST -->
Code that runs on all platforms EXCEPT the custom platform
<!-- #endif -->
```

## Built-in vs Custom Constants

Custom platforms inherit from their base platform. When you extend `mp-dingtalk` on top of `mp-alipay`:

| Directive | Matches | Includes custom? |
|-----------|---------|------------------|
| `#ifdef MP` | All mini-program platforms | Yes (includes DingTalk) |
| `#ifdef MP-ALIPAY` | Alipay base platform | Yes (includes DingTalk) |
| `#ifdef MP-DINGTALK` | DingTalk custom platform only | DingTalk only |

## Example

Given a custom `mp-dingtalk` platform based on `mp-alipay` with `define: { "MP-DINGTALK": true }`:

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

Given a custom `h5-weixin` platform based on `h5` with `define: { "H5-WEIXIN": true }`:

```javascript
// #ifdef H5
H5平台通用代码（含微信服务号）
// #endif

// #ifdef H5-WEIXIN
微信服务号特有代码
// #endif
```

## Best Practices

- Use uppercase for custom constants to match uni-app convention
- Place custom platform code after base platform code for readability
- Test on both the base platform and custom platform to ensure condition compilation works as expected
