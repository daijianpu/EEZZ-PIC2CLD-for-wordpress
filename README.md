# EEZZ-PIC2CLD-for-wordpress
This is the official English documentation for **EEZZ PIC2CLD Professional**, designed for GitHub deployment. It adheres to the 2026 ICC Engineering Standards (PHP 8.4+).

---
<img width="1156" height="730" alt="697d21b62a436a2b2a67d1f04c62c7c1_screenshot-1_raw=true" src="https://github.com/user-attachments/assets/ee37851e-fb58-48f0-bfb8-c1633bb1d876" />

<img width="1157" height="668" alt="1987a9a5e99d378dd451408511d0d696_screenshot-2_raw=true" src="https://github.com/user-attachments/assets/95191c3b-ad6f-4380-9300-04949a78a5e8" />

# EEZZ PIC2CLD Professional - Industrial R2 Core

An industrial-grade Cloudflare R2 storage integration for WordPress. This plugin eliminates local storage bloat by offloading media assets to R2 buckets using high-performance AWS V4 signing and REST API gateways.

## 1. Features

* **Zero-Bloat Architecture**: Hijacks the WordPress media workflow. Images are stored in R2, and URLs are served via Cloudflare Public URLs, keeping your local server clean.
* **AWS V4 Signature Protocol**: Implements rigorous security for R2 communication, ensuring all `PUT` requests are signed with time-sensitive credentials.
* **REST API Gateway**: Features a dedicated endpoint (`/eezzpic2cld/v1/upload`) for handling high-concurrency uploads with physical capability checks.
* **Dual Operation Modes**:
    * **Crop & Refine**: Integrated `Cropper.js` terminal for single-image precision before syncing.
    * **Industrial Batch**: Rapid multi-file synchronization without manual intervention.
* **Multi-Bucket Logic**: Support for mounting storage nodes (Free version limited to 1 active bucket).
* **Native Integration**: Seamlessly hooks into `wp_get_attachment_url` and `wp_prepare_attachment_for_js` to ensure cloud images appear correctly in the Media Library.

## 2. Installation

### Requirements
* **PHP**: 8.4+ (Strict types enforced).
* **WordPress**: 6.5+.
* **Extensions**: `curl`, `openssl`, `hash`.

### Deployment
1.  Clone or upload the repository to your `/wp-content/plugins/eezz-pic2cld/` directory.
2.  Ensure the file structure is intact:
    * `eezzpic2cld-main.php` (Bootstrap)
    * `eezzpic2cld-engine.php` (Signer)
    * `eezzpic2cld-api.php` (API Gateway)
    * `eezzpic2cld-admin.php` (Console)
    * `assets/` (Cropper.js dependencies)
3.  Activate the plugin through the WordPress 'Plugins' menu.

## 3. Usage Instructions

### Step 1: Bucket Configuration
1.  Navigate to **EEZZ Upload -> Bucket Management**.
2.  Input your Cloudflare R2 credentials:
    * **Account ID**: Found in your Cloudflare dashboard.
    * **Access/Secret Keys**: Generated from R2 API tokens.
    * **Public URL**: Your custom domain or R2.dev URL.
3.  Click **Save & Mount**.

### Step 2: Uploading Assets
1.  Go to **EEZZ Upload**.
2.  Select your **Target Bucket**.
3.  **For Single Images**: Use the "Crop & Refine" zone to adjust dimensions. Click "Confirm & Sync" to push to R2.
4.  **For Multiple Images**: Drag and drop into the "Industrial Batch" zone for automated synchronization.

### Step 3: Managing Media
* Assets will appear in the **WordPress Media Library**.
* All generated URLs will point directly to your R2 public endpoint.
* Metadata (width/height) is stored locally for theme compatibility, while physical binaries remain in the cloud.

---
**Security Note**: Sensitive keys are stored in the `wp_options` table. Ensure your database is secured. Professional redundancy and migration tools are locked to the PRO version.

中文版说明
这是为 GitHub 部署准备的 **EEZZ PIC2CLD Professional** 官方中文说明书。本手册遵循 2026 ICC 工程标准（PHP 8.4+）。

---

# EEZZ PIC2CLD Professional - 工业级 R2 云存储核心

一款专为 WordPress 设计的工业级 Cloudflare R2 存储集成插件。通过高性能 AWS V4 签名协议与 REST API 网关，将媒体资产完全卸载至 R2 存储桶，彻底消除本地服务器的存储负担。

## 1. 功能特性

* **零冗余架构**：深度接管 WordPress 媒体工作流。图片物理存储于 R2，通过 Cloudflare 公网 URL 直接提供服务，保持本地服务器磁盘洁净。
* **AWS V4 签名协议**：为 R2 通讯实现严苛的安全加密，确保所有 `PUT` 请求均通过时效性凭证进行签名。
* **REST API 网关**：提供专用端点 (`/eezzpic2cld/v1/upload`)，具备物理级权限校验，支持高并发上传处理。
* **双操作模式**：
    * **裁剪精修 (Single)**：集成 `Cropper.js` 终端，在同步到云端前进行像素级精确裁剪。
    * **工业级批量同步 (Batch)**：无需人工干预的自动化多文件快速同步。
* **多桶管理逻辑**：支持挂载多个存储节点（免费版限制为 1 个激活存储桶）。
* **原生无缝集成**：通过挂载 `wp_get_attachment_url` 与 `wp_prepare_attachment_for_js` 过滤器，确保云端图片在 WordPress 媒体库中完美呈现预览。

---

## 2. 安装说明

### 环境要求
* **PHP**: 8.4+ (强制执行严格类型)。
* **WordPress**: 6.5+。
* **核心扩展**: `curl`, `openssl`, `hash`。

### 部署流程
1.  将仓库代码克隆或上传至 `/wp-content/plugins/eezz-pic2cld/` 目录。
2.  核对物理文件结构完整性：
    * `eezzpic2cld-main.php` (引导模块)
    * `eezzpic2cld-engine.php` (签名引擎)
    * `eezzpic2cld-api.php` (API 网关)
    * `eezzpic2cld-admin.php` (管理终端)
    * `assets/` (Cropper.js 依赖资源)
3.  通过 WordPress 后台“插件”菜单激活插件。

---

## 3. 使用指南

### 第一步：存储桶配置
1.  导航至 **EEZZ Upload -> Bucket Management**。
2.  输入你的 Cloudflare R2 凭证：
    * **Account ID**: 在 Cloudflare 控制面板获取。
    * **Access/Secret Keys**: 通过 R2 API 令牌生成。
    * **Public URL**: 你的自定义域名或 R2.dev 分配的 URL。
3.  点击 **Save & Mount (保存并挂载)**。

### 第二步：上传资产
1.  进入 **EEZZ Upload** 终端。
2.  选择你的 **目标存储桶 (Target Bucket)**。
3.  **单图处理**：使用“裁剪精修”区调整尺寸，点击“确认并同步”推送到 R2。
4.  **批量处理**：将多个图片拖入“工业级批量同步”区，执行自动化同步。

### 第三步：媒体管理
* 所有资产将同步显示在 **WordPress 媒体库** 中。
* 生成的图片 URL 将直接指向你的 R2 公网端点。
* 图片的尺寸等元数据（Metadata）存储于本地以确保主题兼容性，而物理二进制文件则安全托管于云端。

---

**安全提示**：敏感密钥存储于 `wp_options` 表中，请确保数据库安全。专业级的冗余备份与一键迁移工具仅在 PRO 版本中提供。
