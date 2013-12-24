wget progress bar patch
===

This patch makes wget uses a smaller and less informative progress bar when downloading some file from a URL like this:
```
$ wget -nv  http://ftp.gnu.org/gnu/wget/wget-1.14.tar.xz
100%[==============================================================>] 1,584,060    147KB/s   in 12s    

2013-12-24 03:10:29 URL:http://ftp.gnu.org/gnu/wget/wget-1.14.tar.xz [1584060/1584060] -> "wget-1.14.tar.xz.1" [1]
```
instead of:
```
$ wget http://ftp.gnu.org/gnu/wget/wget-1.14.tar.xz
--2013-12-24 03:09:30--  http://ftp.gnu.org/gnu/wget/wget-1.14.tar.xz
Resolving ftp.gnu.org (ftp.gnu.org)... 208.118.235.20, 2001:4830:134:3::b
Connecting to ftp.gnu.org (ftp.gnu.org)|208.118.235.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1584060 (1.5M) [application/x-tar]
Saving to: ‘wget-1.14.tar.xz’

100%[==============================================================>] 1,584,060    137KB/s   in 12s    

2013-12-24 03:09:43 (128 KB/s) - ‘wget-1.14.tar.xz’ saved [1584060/1584060]

```


The idea came from the original pacman downloader, as it produces just the neede output. However, if one uses wget as an external downloader on ```XferCommand```, lots of outputs are printed.

Then, [this post](http://mytechrants.wordpress.com/2009/11/26/wget-add-progressbar-nv/) came with a smart solution, patching wget to have a better output when using the ```-nv -no-verbose``` option.

I just made a small fix in the patch and PKGBUILD to match the more up-to-date [wget-git](https://aur.archlinux.org/packages/wget-git/) package.
