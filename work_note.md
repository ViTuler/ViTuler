### Python

#### Doc String(PEP 257)

Example FTP Downloader

```python
import ftplib

class FTPClient:
    """
    A simple FTP client to connect to an FTP server and check the existence of files or directories.

    This class allows connecting to an FTP server using login credentials,
    checking whether a given path is a file or folder, and closing the connection when done.
    
    Example:
        client = FTPClient('ftp.example.com', 'user', 'password')
        result = client.check_path('/path/to/check')
        client.close()
    """

    def __init__(self, ftp_server: str, user: str, passwd: str, timeout: int = None):
        """
        Initialize the FTPClient with the given FTP server address and user credentials.

        Parameters:
        ftp_server (str): The address of the FTP server to connect to.
        user (str): The username for FTP login.
        passwd (str): The password for FTP login.
        timeout (int, optional): Connection timeout in seconds. Defaults to None.

        Raises:
        ftplib.all_errors: Any error that occurs during the connection process will be raised.
        """
        self.ftp = ftplib.FTP(ftp_server, user=user, passwd=passwd, timeout=timeout)

       def check_path(path: str, detailed: bool = False) -> str | dict:
        """
        Check if a path on the FTP server is a file or directory, and optionally return more details.
    
        Parameters:
        path (str): The path on the FTP server to check.
        detailed (bool, optional): If True, returns additional details like path type and size. Defaults to False.
    
        Returns:
        str: 
            - 'folder' if the path is a directory.
            - 'file' if the path is a file.
            - 'path does not exist' if the path is invalid.
        dict: 
            If `detailed` is True, returns a dictionary with additional details:
            - 'type': Either 'folder' or 'file'.
            - 'size': The size of the file (if it is a file, not applicable for directories).
        
        Raises:
        ftplib.error_perm: If an error occurs during the FTP command.
        """
        try:
            # Check if the path is a folder
            self.ftp.cwd(path)
            if detailed:
                return {'type': 'folder'}
            return 'folder'
        except ftplib.error_perm as e:
            if str(e).startswith('550'):
                try:
                    # Check if it's a file by getting its size
                    size = self.ftp.size(path)
                    if detailed:
                        return {'type': 'file', 'size': size}
                    return 'file'
                except ftplib.error_perm:
                    return 'path does not exist'
        except Exception as e:
            return f'error occurred: {str(e)}'


    def close(self):
        """
        Close the FTP connection.

        This method safely closes the FTP connection established during the object initialization.

        Example:
            client.close()
        """
        self.ftp.quit()

# Example of usage:
if __name__ == "__main__":
      url_para = {
          'user': 'username',
          'pw': 'password',
          'timeout': 30
      }
    
    ftp_client = FTPClient('ftp.example.com', url_para.get('user'), url_para.get('pw'), url_para.get('timeout'))

    path = '/path/to/check'
    result = ftp_client.check_path(path)

    print(f"Path '{path}' is a {result}.")  # Output will be 'folder', 'file', or 'path does not exist'

    ftp_client.close()

```
### CSS 
  
  
#### 
  
  [Navbar Effect](https://element-plus.org/zh-CN/guide/namespace.html#%E8%AE%BE%E7%BD%AE-elconfigprovider)

  ```scss
  .navbar-wrapper {
    position: relative;
    border-bottom: 1px solid var(--border-color);
    height: var(--header-height);
    padding: 0 12px 0 24px;
    background-image: radial-gradient(transparent 1px,var(--bg-color) 1px);
    background-size: 4px 4px;
    backdrop-filter: saturate(50%) blur(4px);
    -webkit-backdrop-filter: saturate(50%) blur(4px);
    top: 0
  }
  ```
  
  最主要的有三个:
  1. background-image 的 径向渐变
  2. background-size 限制单元的大小
  3. backdrop-filter 的毛玻璃

  Blog: [V2](https://www.v2ex.com/t/1079493)
