# 📦 WordPress Base Image (Enterprise)

A highly optimized and hardened base image for enterprise WordPress deployments. Designed to be used in conjunction with a Kubernetes-based hosting platform.

## 🚀 Technical Highlights

- **PHP 8.x Optimized**: Fine-tuned for performance and security.
- **Hardened**: Removed unnecessary packages and configured secure defaults.
- **Build-ready**: Includes essential tools like `wp-cli` for automated management.
- **Cloud Native**: Pre-configured for Azure/AWS persistent storage mounting.

## 🧱 Ecosystem Integration

This base image is designed to power the **[WordPress Enterprise Boilerplate](https://github.com/chinmaymjog/wp-boilerplate)**.

## 🛠️ Usage

Use this image as the `FROM` instruction in your application Dockerfile:

```dockerfile
FROM chinmaymjog/wp-base:latest
COPY ./src /var/www/html
```

## 🛡️ License
Distributed under the MIT License. See `LICENSE` for more information.