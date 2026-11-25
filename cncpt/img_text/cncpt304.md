# Description of the illustration cncpt304.eps

This graphic depicts the buffer search order described in the preceding text. The extended buffer cache includes both the in-memory buffer cache, which contains whole buffers, and the flash cache, which contains buffer bodies. The server process looks in the in-memory cache for the buffer (arrow 1), then the flash cache (arrow 2), and finally reads the buffer from magnetic disk (arrow 3).
