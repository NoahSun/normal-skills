---
name: uni-app-custom-cli-commands
description: Run and build custom platforms via npm run dev:custom and build:custom
---

# CLI Commands

After defining a custom platform in `package.json`, use the uni-app CLI to compile for it.

## vue-cli Commands

For projects using vue-cli, run the custom platform via:

```bash
# Development mode
npm run dev:custom <custom-platform>

# Build mode (release)
npm run build:custom <custom-platform>
```

`<custom-platform>` is the key defined under `uni-app.scripts` in `package.json`.

## Examples

### DingTalk Mini Program

```bash
npm run dev:custom mp-dingtalk
npm run build:custom mp-dingtalk
```

### WeChat Service Account

```bash
npm run dev:custom h5-weixin
npm run build:custom h5-weixin
```

## HBuilderX

HBuilderX automatically reads the `package.json` extension config and generates custom menu items under the **Run** and **Release** menus. Click the corresponding menu (e.g. "钉钉小程序" / "微信服务号") to compile and run.

## Output Directory

The compilation output directory follows the **base platform**, not the custom platform name:

| Custom Platform | Base Platform | Output Directory |
|----------------|--------------|-----------------|
| `mp-dingtalk` | `mp-alipay` | `dist/dev/mp-alipay` (or `mp-alipay`) |
| `h5-weixin` | `h5` | `dist/dev/h5` |

## Tips

- For DingTalk: the output is still in the `mp-alipay` directory. Open it via Alipay Dev Tools, select "DingTalk Mini Program", then open the directory to preview and publish.
- For WeChat service account: open the compiled `h5` output in the target browser.
