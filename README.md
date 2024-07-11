# libdmtx
libdmtx 是一個開源的庫，用於讀寫 Data Matrix 條碼。Data Matrix 條碼是一種二維條碼，廣泛應用於工業和商業領域，用於在小型條碼中編碼大量數據。libdmtx 提供了編寫和解碼這些條碼的工具和功能。該庫是用 C 語言編寫的，並提供了 C API，使其可以被整合到各種應用程序中。此外，還有一些基於 libdmtx 的封裝和綁定，允許在其他編程語言（如 Python）中使用這些功能。

以下提供了分別在Windows和Linux系統下的安裝方式
***

## 1. Installing libdmtx on Windows using MinGW and MSYS

### 1. 下載MinGW 和 MSYS
> MinGW (Minimalist GNU for Windows) 是一個開源的軟體開發工具包，旨在為 Windows 平台提供類似於 Unix 環境下的開發工具和編譯器。它的目標是允許開發者在 Windows 上使用 GNU 工具集（如 GCC）來編譯和運行原生的 GNU/Linux 或 Unix 軟體。
> 而 MSYS（Minimal System）是一個輕量級的模擬 Unix 環境，旨在為 Windows 系統提供一個類 Unix 的開發和執行環境。它是 MinGW（Minimalist GNU for Windows）項目的一部分，通常與 MinGW 一起使用，用於在 Windows 平台上進行程式碼開發和編譯。

* 1. 安裝MinGW
 
to be conti

* 2. 安裝MSYS
 
到[MSYS官網](https://packages.msys2.org/package/autogen)，點擊安裝鍵。
![image](https://github.com/ChengHsunTai/libdmtx/assets/137912642/6f4f9d32-6a97-4210-8eb9-6bb174d2fd69)

安裝完後將會跳出Msys2的終端機視窗

接下來將利用pacman 指令更新套件。
>pacman 是 Arch Linux 的預設套件管理器，也被 MSYS2 用來最為管理系統，接下來會示範一些常用的基本功能。

```
pacman -Syu
```

第一次執行 MSYS2 通常都會先更新套件至最新版本，y 代表的是更新軟體資料庫 u 代表的是更新套件。
>執行這行就像 Ubuntu 中 apt update 再 apt upgrade。


* 3. git clone libdmtx

 安裝git
```
pacman -S git
```

下載 libdmtx 

```
git clone https://github.com/dmtx/libdmtx.git
```
在當前目錄下創建一個名為 libdmtx 的子目錄，其中包含儲存庫的所有文件。

* 4. 安裝 autotools 和其他依賴項
 
```
pacman -S base-devel autoconf automake libtool pkgconf
```
通常 GCC 會包含在 `base-devel`，若仍無法執行GCC(`command not found`)，則另外安裝 GCC:

```
pacman -S gcc
```

* 5. 執行 `./autogen.sh`，如果儲存庫中沒有 configure 腳本，運行 autogen.sh 來生成它
 
在libdmtx的資料夾下執行
 
```
./autogen.sh
```

![image](https://github.com/ChengHsunTai/libdmtx/assets/137912642/930c35e5-f63d-41c3-8373-fb946d306570)

* 6. 運行 configure
 
```
./configure
```

![image](https://github.com/ChengHsunTai/libdmtx/assets/137912642/f831488e-cada-403f-bd61-c06e89d33139)

* 7. 編譯及安裝
 
使用`make`指令進行編譯
```
make
```

這會根據`configure`腳本生成的配置文件來編譯 libdmtx。

![image](https://github.com/ChengHsunTai/libdmtx/assets/137912642/4dcd3a17-9dd2-498a-9ec2-b45a79b4730c)

再來進行安裝

```
make install
```
![image](https://github.com/ChengHsunTai/libdmtx/assets/137912642/68678495-475b-4760-8cf2-8e0dff131f13)

若想確認是否安裝正確，可以輸入以下指令
```
make check
```
![image](https://github.com/ChengHsunTai/libdmtx/assets/137912642/01a2c139-9dd0-4511-98ca-760e0ae14beb)

