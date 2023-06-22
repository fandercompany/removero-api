# Removero API
## __Free__ API to remove background from your photo

[![Python Powered](https://www.python.org/static/img/psf-logo@2x.png)](https://www.python.org/)

[![Build Status](https://raw.githubusercontent.com/fandercompany/removero-api/main/build.svg)](https://removero.serveo.net/)

Removero API is the fastest background removal API that handles almost any image and returns the image in the best quality.

- Free
- Simple
- Site
- API

## Requirements

Dillinger is currently extended with the following plugins.
Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| RemBG | [https://pypi.org/project/rembg/][PlDb] |
| Flask | [https://pypi.org/project/Flask/][PlGh] |
| Werkzeug | [https://pypi.org/project/Werkzeug/][PlGd] |
| Requests | [https://pypi.org/project/requests][PlOd] |

## How to use
#### Python example

Install ```request``` for make request to API

```sh
pip install requests
```

Make a request

```sh
import requests

url = 'https://apiremovero.serveo.net/api/remove_background'

with open('anime.jpg', 'rb') as image_file:
    files = {'image': image_file}
    response = requests.post(url, files=files)

    if response.status_code == 200:
        result = response.json()
        result_filename = result['result']
        print(f'Result filename: {result_filename}')
    else:
        print('Error occurred:', response.text)
```

#### JS example

```sh
const fetch = require('node-fetch');
const fs = require('fs');

const url = 'https://apiremovero.serveo.net/api/remove_background';
const imageFilePath = './anime.jpg';

fs.readFile(imageFilePath, (err, imageBuffer) => {
  if (err) {
    console.error('Error reading image:', err);
    return;
  }

  const formData = new FormData();
  formData.append('image', imageBuffer, { filename: 'anime.jpg' });

  fetch(url, {
    method: 'POST',
    body: formData,
  })
    .then((response) => {
      if (response.status === 200) {
        return response.json();
      } else {
        throw new Error(`Request failed with status ${response.status}`);
      }
    })
    .then((result) => {
      const resultFilename = result.result;
      console.log(`result filename: ${resultFilename}`);
    })
    .catch((error) => {
      console.error('An error occurred:', error);
    });
});


```
### Input 
[![Input](https://apiremovero.serveo.net/static/anime.jpg)](https://apiremovero.serveo.net/static/anime.jpg)

### Output
[![output](https://apiremovero.serveo.net/static/result_anime.jpg)](https://apiremovero.serveo.net/static/anime.jpg)


