# afafa

"""
afaf
"""


- hi
  - hi


***bold***

```c
typedef enum {
    CAMSTREAM_TRANSPORT_RTP_UDP = 0,
    CAMSTREAM_TRANSPORT_MPEGTS_UDP,
    CAMSTREAM_TRANSPORT_SRT,
} CamstreamTransport;

typedef struct CamstreamConfig {
    /* Capture (sender only) */
    const char *input_format;   /* e.g. "v4l2", "dshow", "avfoundation"     */
    const char *device;         /* e.g. "/dev/video0"                       */
    int  width;
    int  height;
    int  fps;
    const char *pixel_format;   /* requested capture pixel format or NULL   */

    /* Encode (sender only) */
    const char *codec;          /* "h264", "hevc"                           */
    const char *hwaccel;        /* "auto", "nvenc", "vaapi", "videotoolbox",
                                   "qsv", "none"                            */
    int  bitrate_kbps;
    int  gop_size;
    int  zero_latency;          /* 1 = tune=zerolatency                     */

    /* Network */
    const char *dest_host;      /* sender: destination, receiver: bind addr */
    int  port;                  /* RTP/SRT/MPEG-TS port                     */
    int  tick_port;             /* companion latency tick port (UDP)        */
    CamstreamTransport transport;

    /* Receiver */
    int  no_display;            /* 1 = decode-only (benchmark) mode         */
    int  low_delay;             /* AV_CODEC_FLAG_LOW_DELAY                  */

    /* Diagnostics */
    int  stats_interval_ms;
    int  verbose;
} CamstreamConfig;

```
