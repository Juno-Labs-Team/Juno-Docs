---
layout: page
title: API Reference
permalink: /api-reference/
nav_order: 4
---

# API Reference

Complete reference for Juno's API.

## Core API

### `juno.create(options)`

Creates a new Juno instance.

**Parameters:**
- `options` (Object) - Configuration options

**Returns:** Juno instance

**Example:**
```javascript
const juno = require('juno')

const app = juno.create({
  port: 3000,
  mode: 'development'
})
```

### `juno.use(plugin, options)`

Registers a plugin with the Juno instance.

**Parameters:**
- `plugin` (Function|Object) - Plugin to register
- `options` (Object) - Plugin options

**Example:**
```javascript
app.use(require('@juno/plugin-router'), {
  routes: './routes'
})
```

## CLI Commands

### `juno create <name>`

Creates a new Juno project.

**Options:**
- `--template <template>` - Project template to use
- `--no-install` - Skip dependency installation

### `juno dev`

Starts development server.

**Options:**
- `--port <port>` - Server port (default: 3000)
- `--host <host>` - Server host (default: localhost)
- `--open` - Open browser automatically

### `juno build`

Builds project for production.

**Options:**
- `--output <dir>` - Output directory (default: dist)
- `--analyze` - Analyze bundle size

## Utilities

### `juno.utils.logger`

Built-in logging utility.

```javascript
const { logger } = require('juno/utils')

logger.info('Information message')
logger.warn('Warning message')
logger.error('Error message')
```

### `juno.utils.config`

Configuration management utility.

```javascript
const { config } = require('juno/utils')

const value = config.get('key', 'defaultValue')
config.set('key', 'value')
```