---
layout: page
title: Troubleshooting
permalink: /troubleshooting/
nav_order: 5
---

# Troubleshooting

Common issues and their solutions.

## Installation Issues

### Permission Errors

If you encounter permission errors during installation:

```bash
# Use sudo (not recommended)
sudo npm install -g juno-cli

# Or configure npm to use a different directory
npm config set prefix ~/.npm-global
export PATH=~/.npm-global/bin:$PATH
```

### Node Version Conflicts

Juno requires Node.js 16.0 or higher:

```bash
# Check your Node version
node --version

# Update Node.js using nvm
nvm install 16
nvm use 16
```

## Development Issues

### Port Already in Use

```bash
# Find process using port 3000
lsof -ti:3000

# Kill the process
kill -9 $(lsof -ti:3000)

# Or use a different port
juno dev --port 3001
```

### Build Failures

#### Memory Issues

```bash
# Increase Node.js memory limit
export NODE_OPTIONS="--max-old-space-size=4096"
juno build
```

#### Dependency Conflicts

```bash
# Clear npm cache
npm cache clean --force

# Remove node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

## Common Error Messages

### `Error: Cannot find module 'juno'`

**Cause:** Juno is not installed or not in PATH.

**Solution:**
```bash
npm install -g juno-cli
# or
npm install juno --save
```

### `Error: Port 3000 is already in use`

**Cause:** Another process is using the same port.

**Solution:**
```bash
juno dev --port 3001
```

### `Error: Configuration file not found`

**Cause:** Missing `juno.config.js` file.

**Solution:**
```bash
# Create a basic config file
echo "module.exports = {}" > juno.config.js
```

## Getting Help

If you're still experiencing issues:

1. Check the [GitHub Issues](https://github.com/juno-labs/juno/issues)
2. Search [GitHub Discussions](https://github.com/juno-labs/juno/discussions)
3. Create a new issue with:
   - Juno version (`juno --version`)
   - Node.js version (`node --version`)
   - Operating system
   - Complete error message
   - Steps to reproduce