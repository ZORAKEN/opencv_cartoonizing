import cv2


def cartoon_frame(frame):
    """
    Apply cartoon effect to a single frame.
    """

    # 1. Convert to grayscale
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

    # 2. Blur to reduce noise
    gray = cv2.medianBlur(gray, 5)

    # 3. Detect edges
    edges = cv2.adaptiveThreshold(
        gray,
        255,
        cv2.ADAPTIVE_THRESH_MEAN_C,
        cv2.THRESH_BINARY,
        9,
        9
    )

    # 4. Smooth colors
    color = cv2.bilateralFilter(frame, 9, 250, 250)

    # 5. Combine edges + color
    cartoon = cv2.bitwise_and(color, color, mask=edges)

    return cartoon


def run_webcam_cartoon():
    """
    Capture webcam feed and apply cartoon filter in real time.
    """

    cap = cv2.VideoCapture(0)

    if not cap.isOpened():
        print("[ERROR] Cannot access webcam")
        return

    print("[INFO] Press 'q' to exit")

    while True:
        ret, frame = cap.read()

        if not ret:
            print("[ERROR] Failed to grab frame")
            break

        # Flip horizontally for mirror effect (optional but nicer UX)
        frame = cv2.flip(frame, 1)

        # Apply cartoon filter
        cartoon = cartoon_frame(frame)

        # Show result
        cv2.imshow("Webcam Cartoon Filter", cartoon)

        # Exit on 'q'
        if cv2.waitKey(1) & 0xFF == ord('q'):
            break

    cap.release()
    cv2.destroyAllWindows()
    print("[INFO] Webcam closed")


if __name__ == "__main__":
    run_webcam_cartoon()
