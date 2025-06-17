---
layout: page
title: Configuration
permalink: /configuration/
nav_order: 3
---

# Configuration

Juno can be configured through various methods to suit your project's needs.

## Configuration File

The main configuration file is `juno.config.js` located in your project root:

```javascript
// juno.config.js
module.exports = {
  // Basic settings
  port: 3000,
  host: 'localhost',
  
  // Build configuration
  build: {
    outDir: 'dist',
    sourcemap: true,
    minify: true
  },
  
  // Development settings
  dev: {
    open: true,
    hot: true
  },
  
  // Plugin configuration
  plugins: [
    // Add your plugins here
  ]
}
```

## Environment Variables

Configure Juno using environment variables:

| Variable | Description | Default |
|----------|-------------|---------|
| `JUNO_PORT` | Server port | `3000` |
| `JUNO_HOST` | Server host | `localhost` |
| `JUNO_ENV` | Environment mode | `development` |

## Basic Setup

### Development Mode

```bash
juno dev --port 8080 --host 0.0.0.0
```

### Production Build

```bash
juno build --output dist
```

## Advanced Configuration

### Custom Webpack Config

```javascript
// juno.config.js
module.exports = {
  webpack: (config, { dev, isServer }) => {
    // Modify webpack config
    return config
  }
}
```

### Plugin System

```javascript
// juno.config.js
module.exports = {
  plugins: [
    '@juno/plugin-typescript',
    '@juno/plugin-sass',
    {
      name: '@juno/plugin-custom',
      options: {
        customOption: true
      }
    }
  ]
}
```