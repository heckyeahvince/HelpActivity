# Help Activity Demo 

This assignment presents a basic Help activity implementation using text from a raw file.


## Problem:

Design and implement an Android Help activity utilizing a text file in the raw directory.   

## Keypoints:

File access:
```Java
 // Read raw file into string and populate TextView
        InputStream iFile = getResources().openRawResource(R.raw.help);
        try {
            TextView helpText = (TextView) findViewById(R.id.TextView_HelpText);
            String strFile = inputStreamToString(iFile);
            helpText.setText(strFile);
        } catch (Exception e) {
            // Handle Exception, i.e. toast cannot open file
        }
```

Extract the String:
```Java
  public String inputStreamToString(InputStream is) throws IOException {
        StringBuffer sBuffer = new StringBuffer();
        DataInputStream dataIO = new DataInputStream(is);
        String strLine = null;

        while ((strLine = dataIO.readLine()) != null) {
            sBuffer.append(strLine + "\n");
        }

        dataIO.close();
        is.close();

        return sBuffer.toString();
    }
```

Sample help.txt in the raw directory:
```text
HELP DEMO v1.0 (Alpha)


HELP DEMO v1.0 /* Give a background of the app */


INSTRUCTIONS:

/* Give the instructions for the app */


FEATURES:
- ...
/* Give the features of the app */ 


SUPPORT INFORMATION:

/* APP NAME */ is developed by MKC.

Melvin K. Cabatuan
Phone: (+63)999-522-6213
Email: melvincabatuan@gmail.com
All Rights Reserved
```
