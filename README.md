# ZXing QR-Code Sample App in Android (Kotlin)
This is a Sample app to generate QR-Code using ZXing library in Kotlin.
## Screenshots
![screen](../master/screenshots/screen.png)

## Step 1 : Add dependency
```groovy
    implementation 'com.google.zxing:core:3.4.1'
```

## Step 2 : Add this method
```kotlin
// copy this method to your class
private fun generateQRCode(text: String): Bitmap {
        val width = 500
        val height = 500
        val bitmap = Bitmap.createBitmap(width, height, Bitmap.Config.ARGB_8888)
        val codeWriter = MultiFormatWriter()
        try {
            val bitMatrix = codeWriter.encode(text, BarcodeFormat.QR_CODE, width, height)
            for (x in 0 until width) {
                for (y in 0 until height) {
                    bitmap.setPixel(x, y, if (bitMatrix[x, y]) Color.BLACK else Color.WHITE)
                }
            }
        } catch (e: WriterException) { Log.d(TAG, "generateQRCode: ${e.message}") }
        return bitmap
    }
```

## Step 3 : Use the method
```kotlin
// replace the sample text
val bitmap = generateQRCode("Sample Text")
imageView.setImageBitmap(bitmap)
```

## Buy me a coffee
If this helped you consider [buying me a coffee ](https://www.buymeacoffee.com/riyasv).
