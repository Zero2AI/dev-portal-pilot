# Developers Portal - How To
A list of hello world programs to help you get started with writing your first model package.<br>
`Note` The document expects that the user has python3.6+ and pip installed and setup on the development environment.

### How to Run
The document will demonstrate running *image_to_stats* example under `examples` directory.<br>
Go to `examples/image_to_stats` dir and preferably inside virtual environment install dependencies.
```bash
$ pip install -r requirements.txt
```

Next, open python console and import `main()` function from `app.py`
```py
from app import main
```

As per the example, it expects one input i.e., an image. The image here has to an image object and not a file. That is how the `main` function is defined.<br>
To pass a file object, we can either load it from local disk or download. For this example we will download and load the image using `Pillow` package.
```py
import requests

from PIL import Image

image_url = "http://images.cocodataset.org/val2017/000000039769.jpg"

image = Image.open(requests.get(image_url, stream=True).raw)
```

All that is left is to pass the image object to main function and get the results
```py
stats = main(image)
print(stats)
```

You should expect a list of key value pair objects.

### Full Code
```py
import requests

from app import main
from PIL import Image

image_url = "http://images.cocodataset.org/val2017/000000039769.jpg"

image = Image.open(requests.get(image_url, stream=True).raw)

stats = main(image)
print(stats)
```


