# Write-and-Read-Text-file-in-internal-storege and check Directory storage.
Write and Read Text file in internal storege

== Check Directory Storage ==

 File file = Environment.getDataDirectory();
 StatFs stat = new StatFs(file.getPath());
 long blockSize = stat.getBlockSize();
 long availableBlocks = stat.getAvailableBlocks();
 String total = Formatter.formatFileSize(context, availableBlocks * blockSize);
 double Total = Double.parseDouble(total.replaceAll("[^\\d.]", ""));
 //  Toast.makeText(context, Total+":GB", Toast.LENGTH_SHORT).show();
 double asfarasSpace = 0.2;
 if (Total <= asfarasSpace) {
     Toast.makeText(context, "No More Memory Space Available.", Toast.LENGTH_SHORT).show();
 } else {
     Toast.makeText(context, "More Memory Space Available.", Toast.LENGTH_SHORT).show();
 }
 
== Write ==

 File file = context.getFilesDir();
 File file1 = new File(file, "GPSCordForPoly.txt");
 try {
 FileOutputStream outputStream = new FileOutputStream(file1, true);
 OutputStreamWriter streamWriter = new OutputStreamWriter(outputStream);
 try {
     streamWriter.append(GPSCordWrite);  // streamWriter.write(GPSCordWrite);
     streamWriter.close();
     outputStream.close();
} catch (IOException e) {
      e.printStackTrace();
}
} catch (FileNotFoundException e) {
      e.printStackTrace();
 }
            
== Read ===

 File file = new File(new File("" + context.getFilesDir()), "GPSCordForPoly.txt");
 InputStreamReader inputStreamReader = new InputStreamReader(new FileInputStream(file), "UTF8");
 char[] buffer = new char[1024 * 4];
 StringWriter stringWriter = new StringWriter();
 while (-1 != (n = inputStreamReader.read(buffer))) 
 {
   stringWriter.write(buffer, 0, n);
 }
