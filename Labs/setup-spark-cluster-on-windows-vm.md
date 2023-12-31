# Setup Spark Custer on Windows Machine

## Open Powershell as administrator
## Create directory to store all downloaded files
```
md c:\mydownloads
```

## Install Python
```
cd c:\mydownloads
Invoke-WebRequest -Uri "https://www.python.org/ftp/python/3.11.4/python-3.11.4-amd64.exe" -OutFile "python-3.11.4-amd64.exe"

c:/mydownloads/python-3.11.4-amd64.exe InstallAllUsers=1 PrependPath=1 Include_test=0 /quiet
```

## Create directory structure
```
md c:\hadoop
md c:\hadoop\bin
```

## Downlaod and install Hadoop
```
$url = "https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe"
$dest = "c:\hadoop\bin\winutils.exe"
Invoke-WebRequest -Uri $url -OutFile $dest
```

## Downlaod and install Spark
```
$url = "https://dlcdn.apache.org/spark/spark-3.4.1/spark-3.4.1-bin-hadoop3.tgz"
$dest = "c:\mydownloads\spark-3.4.1-bin-hadoop3.tgz"
Invoke-WebRequest -Uri $url -OutFile $dest
cd c:\mydownloads
tar -xvzf spark-3.4.1-bin-hadoop3.tgz
Move-Item -Path spark-3.4.1-bin-hadoop3 -Destination C:\
ren c:\spark-3.4.1-bin-hadoop3 c:\spark
```

## Downlaod and install Java
```
$url = "https://download.oracle.com/java/20/latest/jdk-20_windows-x64_bin.zip"
$dest = "c:\mydownloads\jdk-20_windows-x64_bin.zip"
Invoke-WebRequest -Uri $url -OutFile $dest
cd c:\mydownloads
Expand-Archive -LiteralPath 'jdk-20_windows-x64_bin.zip' -DestinationPath .
Move-Item -Path jdk-20.0.2 -Destination C:\
ren c:\jdk-20.0.2 c:\jdk
```

## Set environment variables
```
setx /M HADOOP_HOME "c:\hadoop"
setx /M SPARK_HOME "c:\spark"
setx /M JAVA_HOME "c:\jdk"
setx /M PYSPARK_DRIVER_PYTHON "jupyter"
setx /M PYSPARK_DRIVER_PYTHON_OPTS "notebook"
setx /M PYSPARK_PYTHON "python"
```

## Set below path in System Settings using UI
```
%HADOOP_HOME%\bin
%SPARK_HOME%\bin
%JAVA_HOME%\bin
C:\Program Files\Python311\
C:\Program Files\Python311\Scripts\
```

## Close Powershell
```
exit
```

## Open powershell in admin mode
## Check versions
```
python -V
java -version
pyspark --version
```

## Start Spark Cluster
```
spark-class org.apache.spark.deploy.master.Master -h 127.0.0.1
spark-class org.apache.spark.deploy.worker.Worker spark://127.0.0.1:7077 -h 127.0.0.1
spark-class org.apache.spark.deploy.worker.Worker spark://127.0.0.1:7077 -h 127.0.0.1
```

## Open CMD to run below commands

## Create Python Virtual Environment
```
md c:\python_working
cd c:\python_working
python -m venv venv
c:\python_working\venv\Scripts\activate
```

## Instll PySpark libraries in Python
```
cd c:\python_working
c:\python_working\venv\Scripts\activate
pip install pyspark
pip install findspark
```

## Instll Jupyter Notebook in Python
```
c:\python_working\venv\Scripts\activate
pip install jupyter
```

## Start Jupyter Notebook
```
c:\python_working\venv\Scripts\activate
cd c:\python_working
jupyter notebook --ip=0.0.0.0
```
