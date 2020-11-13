# libreoffice-convert #

A simple and fast node.js module for converting office documents to different formats.

## Dependency ##

Please install libreoffice in /Applications (Mac), with your favorite package manager (Linux), or with the msi (Windows).


## Usage example ##
```javascript
import { Converter, ConvertOptions } from './converter'
import * as fs from 'fs';
import * as path from 'path';

const format = '.pdf';
const inputPath = path.join(__dirname, '../resources/hello.docx');
const outputPath = path.join(__dirname, `../resources/hello${format}`);

const options: ConvertOptions = {
    format: format,
    inputPath: inputPath,
    outputPath: outputPath,
    filter: undefined,
}

Converter.convertWithOptions(options).then((result) => {
    if (!result) {
        console.error('Ooops - something went wrong');
    } else {
        // Here in result you have pdf file which you
        // can save or transfer in another stream
        console.log('File converted to: outputPath);
        fs.writeFileSync(outputPath, result);
    }
});
```

