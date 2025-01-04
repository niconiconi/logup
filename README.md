# Logup

[![npm version](https://badge.fury.io/js/logup.svg)](https://badge.fury.io/js/logup)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Logup is a modern, lightweight logging utility designed for JavaScript applications. It provides a flexible and powerful API for managing application logs with features like log levels, custom formatters, and multiple transport options.

## Key Features

- Simple and intuitive API
- Multiple log levels (debug, info, warn, error)
- Custom log formatters
- Multiple transport options (console, file, network)
- Support for async logging
- Structured logging with JSON output
- Log rotation and management
- Minimal dependencies
- TypeScript support

## Installation

```bash
npm install logup
# or
yarn add logup
```

## Quick Start

```javascript
import { Logger } from 'logup';

// Create a new logger instance
const logger = new Logger({
  level: 'info',
  format: 'json'
});

// Start logging!
logger.info('Application started');
logger.warn('Resource running low', { memory: '85%' });
logger.error('Connection failed', new Error('Timeout'));
```

## Configuration

Logup can be customized to suit your needs:

```javascript
const logger = new Logger({
  // Minimum log level to output
  level: 'debug',
  
  // Log format ('simple', 'json', or custom formatter)
  format: 'json',
  
  // Transport options
  transports: [
    new ConsoleTransport(),
    new FileTransport({ filename: 'app.log' })
  ],
  
  // Additional metadata to include with every log
  metadata: {
    app: 'my-service',
    environment: 'production'
  }
});
```

## Log Levels

Logup supports the following log levels (in order of increasing severity):

1. debug - Detailed information for debugging
2. info - General information about application flow
3. warn - Warning messages for potentially harmful situations
4. error - Error messages for serious problems

## Advanced Usage

### Custom Formatters

```javascript
const customFormatter = (log) => {
  return `[${log.timestamp}] ${log.level}: ${log.message}`;
};

const logger = new Logger({
  format: customFormatter
});
```

### Async Logging

```javascript
await logger.asyncLog('info', 'This is an async log message');
```

### Structured Logging

```javascript
logger.info('User action', {
  userId: '123',
  action: 'login',
  duration: 150
});
```

## Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

## License

MIT License - feel free to use this in your own projects.

## Support

- [Documentation](https://logup.dev)
- [GitHub Issues](https://github.com/niconiconi/logup/issues)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/logup)