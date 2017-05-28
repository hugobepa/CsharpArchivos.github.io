## C# Archivos y directorios


### Tratamiento  C#  Archivos y Directorios

- data:text/html, <html contenteditable>

[guia basica markdown](https://github.com/ricval/Documentacion/blob/master/Guias/GitHub/mastering-markdown.md)
[guia completa markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)


[guia C#  file y directorios](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/file-system/how-to-get-information-about-files-folders-and-drives)
[guia C#](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/file-system/)

[Link API  DirectoryInfo](https://msdn.microsoft.com/es-es/library/system.io.directoryinfo(v=vs.110))
[Link  API FileInfo](https://msdn.microsoft.com/es-es/library/system.io.fileinfo(v=vs.110))
[Link  API Directory](https://msdn.microsoft.com/es-es/library/system.io.directory(v=vs.110))
[Link  API Path](https://msdn.microsoft.com/es-es/library/system.io.path(v=vs.110))

### Informacion archivos, carpetas y unidades

#### using

>System.IO.FileInfo
>System.IO.DirectoryInfo
>System.IO.DriveInfo
>System.IO.Directory
>System.IO.File


#### Trabajar con directorio

 >System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");
 
#### Extraer informacionDirectorio

        Console.WriteLine(di.TotalFreeSpace);
        Console.WriteLine(di.VolumeLabel);
        
#### Ruta Directorio

		System.IO.DirectoryInfo dirInfo = di.RootDirectory;
		Console.WriteLine(dirInfo.Attributes.ToString());
    
#### Obtener archivos

        System.IO.FileInfo[] fileNames = dirInfo.GetFiles("*.*");
        
        foreach (System.IO.FileInfo fi in fileNames) fi.Name, fi.LastAccessTime, fi.Length
        
#### SubDirectorios

			System.IO.DirectoryInfo[] dirInfos = dirInfo.GetDirectories("*.*");
  
			foreach (System.IO.DirectoryInfo d in dirInfos)  Console.WriteLine(d.Name);
			
	> catch (System.IO.FileNotFoundException e)
	
####File

	fi = new System.IO.FileInfo(s);  fi.Name, fi.Directory;
	
####Direcory

		> boolean b= !Directory.Exists(@"C:\Users\Public\TestFolder\") or .Exists("C:\\Users\\Public")
		
####Crear Subdirectorio

		> string folderName = @"c:\Top-Level Folder";
        > string pathString = System.IO.Path.Combine(folderName, "SubFolder"); 
        > System.IO.Directory.CreateDirectory(pathString);
        
#### Crear file en Directorio

		> //string fileName = "MyNewFile.txt";  String pathString = System.IO.Path.Combine(pathString, fileName);
		
		>boolean b=!System.IO.File.Exists(pathString);

#### Copiar Archivos de directorio a otro

		>string sourcePath = @"C:\Users\Public\TestFolder\text.txt";
        >string targetPath =  @"C:\Users\Public\TestFolder\SubDir.txt";
        >System.IO.File.Copy(sourceFile, destFile, true);
        
#### Metodo copia archivos 2

		>System.IO.Directory.GetFiles(sourcePath);

            
                >Use static Path methods to extract only the file name from the path.
                >fileName = System.IO.Path.GetFileName(s);
                >file= "txt.doc"
                >destFile = System.IO.Path.Combine(targetPath, fileName);
                >System.IO.File.Copy(file, destFile, true);
