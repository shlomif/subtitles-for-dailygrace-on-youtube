all: copy_subtitles

video:
	youtube-dl -f 43 -l 'https://www.youtube.com/watch?v=21uXcvD5lPs'

ORIG = GRADVICE.srt
DEST = final/$(ORIG)

copy_subtitles: $(DEST)

$(DEST): $(ORIG)
	unix2dos < $< > $@

test: video $(DEST)
	vlc --sub-file $(DEST) *.webm
