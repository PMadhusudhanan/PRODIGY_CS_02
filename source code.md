PRE INSTALLING THE LIBRARY

Before implementing the snippet from the new terminal install pillow library "PIP INSTALL PILLOW" then proceed to your snippet... 
![image](https://github.com/user-attachments/assets/73292714-f50a-4af5-9660-cd734051da6b)
and make sure the image should be in an appropriate path and the path should be copied and used in the correct place

![image](https://github.com/user-attachments/assets/a2c93eb7-a651-43ed-b1fd-0d4aaa3776f0)

    from PIL import Image

    def encrypt_image(image_path, key):
      try:
    # Open the image
    img = Image.open(image_path)
    pixels = img.load()

    # Get image dimensions
    width, height = img.size

    # Encrypt the image by applying a basic mathematical operation to each pixel
    for y in range(height):
        for x in range(width):
            r, g, b = pixels[x, y]
            r = (r + key) % 256
            g = (g + key) % 256
            b = (b + key) % 256
            pixels[x, y] = (r, g, b)

    # Save the encrypted image
    encrypted_image_path = "encrypted__img.png"
    img.save(encrypted_image_path)
    print(f"Image encrypted and saved as {encrypted_image_path}")
    except Exception as e:
    print(f"An error occurred: {e}")

    def decrypt_image(encrypted_image_path, key):
    try:
    # Open the encrypted image
      img = Image.open(encrypted_image_path)
      pixels = img.load()

    # Get image dimensions
      width, height = img.size

    # Decrypt the image by reversing the mathematical operation applied during encryption
    for y in range(height):
        for x in range(width):
            r, g, b = pixels[x, y]
            r = (r - key) % 256
            g = (g - key) % 256
            b = (b - key) % 256
            pixels[x, y] = (r, g, b)

    # Save the decrypted image
    decrypted_image_path = "decrypted_image.png"
    img.save(decrypted_image_path)
    print(f"Image decrypted and saved as {decrypted_image_path}")
    except Exception as e:
      print(f"An error occurred: {e}")

     # Example usage
    image_path = r"C:\Users\Hp\Downloads\images.jpg" # Replace with the path to your image
    encryption_key = 87

    # Encrypt the image
    encrypt_image(image_path, encryption_key)

    # Decrypt the encrypted image
    decrypt_image( "encrypted__img.png", encryption_key)
