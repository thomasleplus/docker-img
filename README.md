# Images

Docker container to manipulate images (imagemagick, exiftool...).

## Example without using the filesystem

Let's say that you have an image `foo.jpg` in your current working directory that you want to extract its metadata:

### Mac/Linux

```
cat foo.jpg | docker run --rm -i --net=none thomasleplus/img identify -
```

### Windows

```
type foo.jpg | docker run --rm -i --net=none thomasleplus/img identify -
```

## Example using the filesystem

Same thing, assuming that you have an image `foo.jpg` in your current working directory that you want to extract its metadata:

### Mac/Linux

```
docker run --rm -it --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" thomasleplus/img identify /tmp/foo.jpg
```

### Windows

In `cmd`:

```
docker run --rm -it --net=none -v "%cd%:/tmp" thomasleplus/img identify /tmp/foo.jpg
```

In PowerShell:

```
docker run --rm -it --net=none -v "${PWD}:/tmp" thomasleplus/img identify /tmp/foo.jpg
```

## Help

To know more command line options of one of the imagemagick command:

```
docker run --rm --net=none thomasleplus/img identify -help
```
