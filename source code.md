# PRE INSTALLING THE LIBRARY
 Before implementing the snippet from the new terminal install pillow library "PIP INSTALL PILLOW" then proceed to your snippet...
 ![image](https://github.com/rocky-2904/PRODIGY_CS_02/assets/173170607/500b65b9-42c5-449d-8b3f-7a91a4bf214e)

 
 and make sure the image should be in an appropriate path and the path should be copied and used in the correct place
   
 ![image](https://github.com/rocky-2904/PRODIGY_CS_02/assets/173170607/be39c528-376e-4ace-ac6c-d939b6ea4dee)
   
    
    
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
