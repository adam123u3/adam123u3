from moviepy.editor import *

# Crear una lista de imágenes para el video
image_files = ['imagen1.jpg', 'imagen2.jpg', 'imagen3.jpg']

# Cargar las imágenes y definir su duración en el video
clips = [ImageClip(image_file, duration=5) for image_file in image_files]

# Crear una composición de video con las imágenes
video = concatenate_videoclips(clips)

# Agregar texto al video
text = TextClip("¡Bienvenido al mundo mágico!", fontsize=30, color='white').set_position('center').set_duration(5)
video = CompositeVideoClip([video, text])

# Agregar música de fondo al video
music = AudioFileClip("musica_fondo.mp3")
video = video.set_audio(music)

# Guardar el video resultante
video.write_videofile("video_magico.mp4", codec='libx264')
