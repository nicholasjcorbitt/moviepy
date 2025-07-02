import moviepy.editor as mp

# Load your video
clip = mp.VideoFileClip("export.mov")

# Get video size
width, height = clip.size

# Create black box for the right third of the screen
dee_box_width = width // 3
black_box = mp.ColorClip(size=(dee_box_width, height), color=(0, 0, 0), duration=clip.duration)
black_box = black_box.set_position(("right", "top"))

# Overlay the black box
final = mp.CompositeVideoClip([clip, black_box])

# Export final video
final.write_videofile("export_no_dee.mp4", codec="libx264", audio_codec="aac")
