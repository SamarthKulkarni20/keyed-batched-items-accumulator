# Keyed Batched Items Accumulator 🎉

![GitHub Release](https://img.shields.io/badge/Release-v1.0.0-blue?style=flat-square&logo=github)

Welcome to the **Keyed Batched Items Accumulator**! This lightweight utility for Node.js projects simplifies the process of accumulating items into fixed-size batches based on their keys. It ensures that items are processed in the order they are inserted, allowing for efficient batch management in real-time applications.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [API Reference](#api-reference)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)
- [Releases](#releases)

## Features

- **Key-Based Accumulation**: Group items by keys for better organization.
- **Fixed-Size Batches**: Automatically manage items into batches of a specified size.
- **Preserved Order**: Maintain the insertion order of items within each key.
- **Streamlined Processing**: Process items in real-time, avoiding the need for post-processing 1D arrays.
- **Lightweight**: Minimal overhead, designed for performance.
- **TypeScript Support**: Written in TypeScript, offering type safety and better developer experience.

## Installation

To get started, install the package via npm:

```bash
npm install keyed-batched-items-accumulator
```

## Usage

Here’s a simple example of how to use the Keyed Batched Items Accumulator in your Node.js project.

```javascript
const { Accumulator } = require('keyed-batched-items-accumulator');

const accumulator = new Accumulator({
  batchSize: 5,
});

accumulator.on('batch', (key, items) => {
  console.log(`Batch for key ${key}:`, items);
});

// Add items to the accumulator
accumulator.add('key1', 'item1');
accumulator.add('key1', 'item2');
accumulator.add('key1', 'item3');
accumulator.add('key1', 'item4');
accumulator.add('key1', 'item5'); // This triggers the batch event
```

## API Reference

### `Accumulator`

#### `new Accumulator(options)`

Creates a new instance of the Accumulator.

**Parameters:**

- `options` (Object): Configuration options.
  - `batchSize` (Number): The maximum number of items in each batch.

#### `accumulator.add(key, item)`

Adds an item to the accumulator under the specified key.

**Parameters:**

- `key` (String): The key under which to accumulate the item.
- `item` (Any): The item to accumulate.

#### Events

- `batch(key, items)`: Emitted when a batch is ready for processing.

## Examples

### Example 1: Basic Usage

```javascript
const { Accumulator } = require('keyed-batched-items-accumulator');

const accumulator = new Accumulator({ batchSize: 3 });

accumulator.on('batch', (key, items) => {
  console.log(`Processed batch for ${key}:`, items);
});

accumulator.add('group1', 'a');
accumulator.add('group1', 'b');
accumulator.add('group1', 'c'); // Triggers batch
accumulator.add('group1', 'd');
```

### Example 2: Multiple Keys

```javascript
const { Accumulator } = require('keyed-batched-items-accumulator');

const accumulator = new Accumulator({ batchSize: 2 });

accumulator.on('batch', (key, items) => {
  console.log(`Batch for ${key}:`, items);
});

accumulator.add('groupA', '1');
accumulator.add('groupA', '2'); // Triggers batch
accumulator.add('groupB', 'X');
accumulator.add('groupB', 'Y'); // Triggers batch
```

## Contributing

We welcome contributions! If you would like to contribute, please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/YourFeature`).
3. Make your changes and commit them (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/YourFeature`).
5. Open a pull request.

Please ensure your code adheres to the project's coding standards and passes all tests.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Releases

To download the latest version of the Keyed Batched Items Accumulator, visit the [Releases](https://github.com/SamarthKulkarni20/keyed-batched-items-accumulator/releases) section.

You can also check for updates and new features in the same section.

## Conclusion

The Keyed Batched Items Accumulator provides a simple yet powerful way to manage items in batches based on keys. Its design focuses on performance and ease of use, making it a great addition to any Node.js project. 

For further information and updates, please visit the [Releases](https://github.com/SamarthKulkarni20/keyed-batched-items-accumulator/releases) section.