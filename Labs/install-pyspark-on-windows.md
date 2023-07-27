# Setup PySpark on Windows

## Environment:
- Windows 11 on Azure with 8 Core/16 GB RAM

## Download Java:
- https://download.oracle.com/java/20/latest/jdk-20_windows-x64_bin.zip

## Extract Java to C:\jdk-20.0.2

## Install Python

## Install pyspark:
```
cd c:\
python -m venv spark_venv
spark_venv\Scripts\activate
pip install pyspark
pip install findspark
```

## Download winutils:
- https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe

## Create Directory for Hadoop
```
md c:\hadoop
md c:\hadoop\bin
```

## Copy winutils.exe to c:\hadoop\bin

## Set Env Variables
- Open Advanced Settings and set below environment variables in User settings
```
HADOOP_HOME: c:\hadoop
JAVA_HOME: C:\jdk-20.0.2
SPARK_HOME: c:\spark_venv\Lib\site-packages\pyspark
PYSPARK_DRIVER_PYTHON: jupyter
PYSPARK_DRIVER_PYTHON_OPTS: 'notebook'
```

```
PATH: %HADOOP_HOME%\bin
PATH: %JAVA_HOME%\bin
PATH: %SPARK_HOME%\bin
```

## Close Command Prompt and Open Again

## Test PySpark
```
spark_venv\Scripts\activate
pyspark
spark.version
exit()
```

## Install Jupyter Notebook
```
pip install jupyter
md c:\working
```

## Start Jupyter
```
cd c:\working
jupyter notebook --ip=0.0.0.0
```

## Open Ports:
- open port no 8888 on Azure
- open port no 8888 on Windows Firewall advanced security