const through = require('through2');
const PluginError = require('plugin-error');

const PLUGIN_NAME = 'gulp-random-color';

function generateRandomColor() {
  return '#' + Math.floor(Math.random() * 16777215).toString(16);
}

function gulpRandomColor(options) {
  options = options || {};

  const placeholder = options.placeholder || '__RANDOM_COLOR__';

  function transform(file, encoding, callback) {
    if (file.isNull()) {
      return callback(null, file);
    }

    if (file.isStream()) {
      return callback(new PluginError(PLUGIN_NAME, 'Streaming not supported'));
    }

    let content = file.contents.toString();

    // Replace the placeholder with the random color
    const randomColor = generateRandomColor();
    content = content.replace(new RegExp(placeholder, 'g'), randomColor);

    // Update the file contents and push it to the stream
    file.contents = Buffer.from(content);
    this.push(file);
    callback();
  }

  return through.obj(transform);
}

module.exports = gulpRandomColor;
