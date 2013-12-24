wget progress bar patch
===

This patch makes wget uses a smaller and less informative progress bar when downloading some file from a URL.

The idea came from the original pacman downloader, as it produces just the output needed. However, if one uses wget as ```XferCommand```, lots of outputs are printed.

Then, [this post](http://mytechrants.wordpress.com/2009/11/26/wget-add-progressbar-nv/) came with a smart solution, patching wget to have a ```-nv -no-verbose``` option.

I just made a small fix in the patch and PKGBUILD to match the more up-to-date [wget-git](https://aur.archlinux.org/packages/wget-git/).
