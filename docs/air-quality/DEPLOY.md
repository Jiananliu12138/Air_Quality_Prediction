# 部署到 GitHub Pages

此页面位于 `docs/air-quality/vienna.html`，可直接通过 GitHub Pages 发布（使用 `docs/` 目录作为站点源）。

快速部署步骤：

1. 在 GitHub 仓库页面进入 `Settings -> Pages`。
2. 选择 `Branch: main` 并把 `Folder` 设置为 `/docs`，保存。
3. 等待几分钟，您站点将可以通过 `https://<your-username>.github.io/<repo-name>/air-quality/vienna.html` 访问。

已知注意事项：
- 页面通过 `raw.githubusercontent.com` 加载以下资源：
  - `notebooks/airquality/vienna_sensors_config.json`（用于生成下拉选项）
  - `notebooks/airquality/air_quality_model/images/*`（展示图片）

如果希望图片和 JSON 在 GitHub Pages 下由同一源提供（避免跨域或 raw.githubusercontent 速率限制），请把 `notebooks/airquality/air_quality_model/images` 和 `notebooks/airquality/vienna_sensors_config.json` 拷贝到 `docs/air-quality/assets/` 目录中，并把页面中的 URL 修改为相对路径（例如 `assets/images/...`）。

快速拷贝命令（从仓库根目录运行）以将图片移动到文档资产目录：

```bash
# 创建目标目录
mkdir -p docs/air-quality/assets/images

# 从当前路径复制图片
cp notebooks/airquality/air_quality_model/images/* docs/air-quality/assets/images/

# 确保传感器 JSON 可用（已添加），否则也复制它
cp notebooks/airquality/vienna_sensors_config.json docs/air-quality/assets/
```
