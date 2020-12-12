# Bonnie++ in a Docker (Alpine)

Image: `ghcr.io/judge2020/docker-bonnie`


[Docker Image](ghcr.io/judge2020/docker-bonnie) with Bonnie++ benchamrk tool. This image is acting like `bonnie++` command and passes all arguments.

### Build

    docker build -t bonnie .

### Basic Usage

    docker run \
      -it \
      --rm \
      ghcr.io/judge2020/docker-bonnie \
        bonnie++ \
        -d /tmp \
        -m TEST \
        -n 0 \
        -r 128M \
        -s 256M \
        -x 1 \
        -u 0:0 \
        -f \
        -b

Output:

    Using uid:0, gid:0.
    Writing intelligently...done
    Rewriting...done
    Reading intelligently...done
    start 'em...done...done...done...
    TEST,256M,,,134335,13,162332,9,,,+++++,+++,1306.7,2,,,,,,,,,,,,,

To generate `html` file with human readable format use the same docker image and run command below using last line of previous command.

example data: `TEST,256M,,,134335,13,162332,9,,,+++++,+++,1306.7,2,,,,,,,,,,,,,`

    docker run \
      -ti \
      --rm \
      -v ${PWD}:/workdir \
      ghcr.io/judge2020/docker-bonnie \
        bash -c 'echo "[RESULT]" | bon_csv2html > /workdir/out.html'

Use file `out.html` and open it with any web-browser to see human readable output.

Example output

![Table](https://raw.githubusercontent.com/pozgo/docker-bonnie/master/images/table.jpg)

## Author

Przemyslaw Ozgo (<linux@ozgo.info>)

Updated by Hunter Ray for v2 and pushed to GitHub Container Registry (https://ghcr.io)
