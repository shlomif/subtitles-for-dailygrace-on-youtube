all: copy_subtitles

VIDEO = DAILY\ GRADVICE-21uXcvD5lPs.webm

video: $(VIDEO)

$(VIDEO):
	youtube-dl -f 43 -l 'https://www.youtube.com/watch?v=21uXcvD5lPs'

ORIG = GRADVICE.srt
DEST = final/$(ORIG)

copy_subtitles: $(DEST)

$(DEST): $(ORIG)
	unix2dos < $< > $@

test: video all
	vlc --sub-file $(DEST) $(VIDEO)
