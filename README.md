
# Tensorflow for Lego object detection

## Requirements

- Tensorflow 1.2.1
- ffmpeg 3.3.3
(Tested on macOS 10.12.6)

## Docker

If you have any difficulty on building a correct Tensorflow environment, you can use the Docker image and the following commands:

```sh
docker-compose up -d
docker exec -it tensorflow-for-lego /bin/bash
learn.sh
python label_image.py evaluation-data/eval2x2.png
exit
docker-compose down
```

## Prepare Training images

Create video of a specific brick, e.g. brick2x4.mov

Move to training-data/brick2x4

Create images (3 per second):

```sh
ffmpeg -i brick2x4.mov -vf fps=3 img%03d.jpg
```

## Start training

```sh
./learn.sh
```

## Predict recognition

```sh
$ python label_image.py evaluation-data/eval2x2.png
brick2x2 (score = 0.67055)
brick2x3 (score = 0.28938)
brick2x4 (score = 0.03470)
brick1x2 (score = 0.00537)
```

## Resources

- See also https://codelabs.developers.google.com/codelabs/tensorflow-for-poets/#0

- The retrain.py script is part of the tensorflow repo

```sh
curl -O https://raw.githubusercontent.com/tensorflow/tensorflow/r1.1/tensorflow/examples/image_retraining/retrain.py
```
