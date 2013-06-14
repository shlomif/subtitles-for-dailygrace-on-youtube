all: copy_subtitles

FLV_VIDEO = GRADVICE.flv
FLV_VIDEO_PROTO = DAILY\ GRADVICE-21uXcvD5lPs.flv
VIDEO = DAILY\ GRADVICE-21uXcvD5lPs.webm
VIDEO_RENAMED = GRADVICE.webm

video: $(VIDEO) $(VIDEO_RENAMED)

$(VIDEO):
	youtube-dl -f 43 -l 'https://www.youtube.com/watch?v=21uXcvD5lPs'

$(VIDEO_RENAMED): $(VIDEO)
	cp -f "$<" "$@"

$(FLV_VIDEO): $(FLV_VIDEO_PROTO)
	cp -f "$<" "$@"

$(FLV_VIDEO_PROTO):
	youtube-dl -f 35 -l 'https://www.youtube.com/watch?v=21uXcvD5lPs'

ORIG = GRADVICE.srt
DEST = final/$(ORIG)

copy_subtitles: $(DEST)

$(DEST): $(ORIG)
	unix2dos < $< > $@

edit: video
	gnome-subtitles "`pwd`/$(ORIG)"

test: video all
	vlc --sub-file $(DEST) $(VIDEO)

upload: video all
	sky up "$(VIDEO)"
	sky up "$(DEST)"

remote_test:
	vlc --sub-file http://www.shlomifish.org/Files/files/video/GRADVICE.srt http://www.shlomifish.org/Files/files/video/DAILY%20GRADVICE-21uXcvD5lPs.webm
