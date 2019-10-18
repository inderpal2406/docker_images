## Lab 18
To demonstrate `ONBUILD` instruction.

* `ONBUILD` is a special instruction, followed by other instructions, such as `RUN`, `COPY`, etc., and these instructions will not be executed when the current image is built.
* Only when the current image is mirrored, the `ONBUILD` instructions will be executed.
* The other instructions in Dockerfile are prepared to customize the current image. Only `ONBUILD` is prepared to help others customize themselves.

**`ONBUILD` is pending to be read.** <br>
Link: https://dockerlabs.collabnix.com/beginners/dockerfile/onbuild.html
