# Background-Subtraction
Background Subtraction
import cv2

def background_subtraction(video_path):
    cap = cv2.VideoCapture(video_path)
    fgbg = cv2.createBackgroundSubtractorMOG2()

    while True:
        ret, frame = cap.read()

        fgmask = fgbg.apply(frame)

        cv2.imshow('Original Frame', frame)
        cv2.imshow('Foreground Mask', fgmask)

        if cv2.waitKey(30) & 0xFF == 27:
            break

    cap.release()
    cv2.destroyAllWindows()

# Example usage
video_path = 'path/to/your/video.mp4'
background_subtraction(video_path)
