####生成SSH公钥
	$ cd ~/.ssh
	$ ls
	authorized_keys2  id_dsa       known_hosts
	config            id_dsa.pu
假如没有这些文件，或者干脆连 `.ssh` 目录都没有，可以用 `ssh-keygen` 来创建。
	
	Lewis:.ssh lewis$ ssh-keygen
	Generating public/private rsa key pair.
	Enter file in which to save the key (/Users/lewis/.ssh/id_rsa):
	Enter passphrase (empty for no passphrase):
	Enter same passphrase again:
	Your identification has been saved in /Users/lewis/.ssh/id_rsa.
	Your public key has been saved in /Users/lewis/.ssh/id_rsa.pub.
	The key fingerprint is:
	SHA256:SwtOsPj+TMrR7tpUxLAtc8kFzPO0HNQK/sypV3Z2gmA lewis@Lewis.local
	The key's randomart image is:
	+---[RSA 2048]----+
	|      .o.oo.     |
	|       *=oo .    |
	|    . +.B* +     |
	|   . o =. E      |
	|  . . o S= o .   |
	|   . + + o= + + .|
	|    o = o. o o o |
	|   o O  . .      |
	|    =+*  .       |
	+----[SHA256]-----+
	
查看密钥：	
	
	Lewis:.ssh lewis$ cat id_rsa.pub
	ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC6POSWs9kzq4QBl4VX64YmLclR+ZdxuzX4tjdMkWFmBU5Hzlqjp9hsxRlxUl5FdI1SzMog18+A/Doi3l5P/a6FTW7ZxrbLGeVBpTJeXDfW7AgMRe8V0WmGwgsmA+8OG31kPZOX2c6ZICBD56cisQzAcpipJuiUXSJGNvFnPm+lB174+A+LJNGYdD/BUIe+k+2CTrGPjNmb/GULIsddqmcfqyQRVqAxJmARmiXXpvI3g1Vi7DR7VDj8FZrr8bAYeMwhPQapb0/BwM/gLLmEuwmLI5FiliJ77BFLElHOwj3XaALiJlLAuwvtUAZ3e+FiXI/KndpgYh5PzT22ZVBVJEnH lewis@Lewis.local
