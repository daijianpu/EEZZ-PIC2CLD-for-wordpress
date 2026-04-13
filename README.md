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
