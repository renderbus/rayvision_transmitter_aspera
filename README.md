rayvision_transmitter_aspera
==============================
### Base usage：

#### Allowed options:
 -h [ --help ]      produce help message, process exit code

 0: success
 
 -1: fatal error
 
 1: should retry.
 
 simple upload dir example:
 
 -E raysync  -H 127.0.0.1 -P 10200 -S 10201 -U 100001 -T upload_path -L /mnt/
 
#### custom log file config:
 
 process will find log.ini from current work dir first, if next two env value not be set.
 
     Env RAYVISION_LOG: path to log dir.
     Env RAYVISION_LOG_INI: full path to log config file.
     log config file content may include:
     log_prefix: set log file name
     min_level: set log level,can be set TRK_LEVEL DBG_LEVEL WAR_LEVEL ERR_LEVEL
     file_size: set per log file size, uint MB, default 10 MB
     log_file_count: set log file count, default 10
     log_path: set log file dir, if env RAYVISION_LOG be set, this will not be use
 
  -v [ --version ]                 show current version.
  
  -E [ --engine ] arg              set engine type:  aspera  raysync
  
  -H [ --host ] arg                transmit server host
  
  -P [ --port ] arg                transmit server port
  
  -S [ --storage ] arg             storage id
  
  -U [ --uid ] arg                 user id
  
  -T [ --type ] arg                transmit type:
                                     1. upload_json: upload from json file,in this type, next remote will not used.
                                     2. upload_list: upload from file list.
                                     3. upload_path: upload a dir or file.
                                     4. download_list: dowload path read from a file.
                                     5. download_path: download a dir or file from remote server.
 
  -L [ --local ] arg               local path: if arg type is be set to upload,
                                   process will upload path or upload file list here, or download file will be saved here
  
  -R [ --remote ] arg (=/)         remote path:
                                     upload: always set to "/" to transmit file to user root
                                     download: remote download path
  
  -r [ --retry ] arg (=2)          error retries, default 2
  
  -K [ --keep ] arg (=0)           set true or false to keep local path level.
  
  -s [ --speed-limit ] arg (=2000) bound limit, unit KB/s, default 2000 KB/s, max speed is 1048576 KB/s,1 Gbps/s
  
  -C [ --config ] arg              local db config path. support sqlite and redis
                                   if local file mtime and size not change,use this can speed up the transmission process
  
  -p [ --protocol ] arg (=2)       engine raysync support this option
                                     0: udp first if udp fail try tcp.
                                     1: udp.
                                     2: tcp.
  
  -c [ --count-ranges ] arg        when arg type is set to upload_list or download_list: 0 100 mean [0,100) defalut all
