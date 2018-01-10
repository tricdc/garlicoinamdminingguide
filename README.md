# Garlicoin AMD mining; a guide by snake [bare minimum]
#### This guide is targeted towards Windows users, YMMV if you are on other systems and you may need to make adjustments.
last updated: 1/9/18
## Pool mining
Pool mining is much easier to setup rather than solo mining. Here's how to do it:

1. Download and extract [yacminer](https://drive.google.com/file/d/1T5P2sm0iYFwGU1kViK7yyKVKsMsULSVg/view?usp=sharing)
2. Open "mine.bat" with notepad
3. Change the Garlicoin address after "-u" to yours and change the stratum address after "-o" to whatever pool you are mining on.

Example:
> yacminer --nscrypt --nfmin 10 --nfmax 10 -o **stratum+tcp://123.45.67.8:3333** -u **myfaRqUQcBR2fGF1hNVTqD1UgWxV1zAfpw** -p x -T -I 15

please note that 123.45.67.8 is not a real server

4. Double click "mine.bat"
5. You now should be mining!

### Notes
* Yacminer is based off of CGMiner so commands should be similar.
* There may be a more efficient command for your system but you have to tweak different settings in order to find it.
***
## Solo mining
Solo mining is trickier to setup as it involves hosting a mining pool on your local network and then mining to it. Luckily, if you are running Windows 10 Pro, Enterprise, or Education you can just download the Docker image and then run it. If not, you're going to have to wait.
### Solo mining (docker setup)
1. Download and install [Docker](https://www.docker.com/docker-windows).
2. Press windows key + r and type in "**powershell**" (no quotes).
3. Run `cd C:\` and `mkdir garlicoin`.
4. Run `cd garlicoin`.
5. Run `notepad garlicoin.conf` and it will ask you if you want to create a new file, say yes.
6. Paste [this](https://pastebin.com/raw/BRGF9DTw) into the file. Then, save and exit.
7. Run `docker pull treetwig/nompgarlicoin:latest`. **This step may take a while**.
8. Run `docker run -it --name=nompgarlicoin -v C:\nompgarlicoin:/root/.garlicoin -p 127.0.0.1:3333:3333 -p 80:80 treetwig/nompgarlicoin:latest`.

*(everything below this point will most likely be simplified some point in the future)*
9. The window should now say:

	> root@[something]:/#

	If it doesn't, try running `docker attach nompgarlicoin`.
    
10. Run `nano ~/nomp/pool_configs/garlicoin.conf`
11. Replace the address with yours. `"address": "myfaRqUQcBR2fGF1hNVTqD1UgWxV1zAfpw",`
12. Set enabled to **true**:
	>"paymentProcessing": {
    >
    >"enabled": **false**,
13. Exit nano with ctrl + x, y, enter
10. To start your pool, issue the following commands:
	1. `redis-server &`
	2. `garlicoind -testnet -connect=52.89.91.13 &`
	3. `cd`
	4. `cd nomp`
	5. `node init`
11. You should now see output in the console.
12. Navigate to [127.0.0.1](http://127.0.0.1) in your browser and verify that NOMP (the pool) is running.
13. To start mining, follow all the same steps as in the section "Pool mining" and set the stratum address to "stratum+tcp://127.0.0.1:3333"
14. You should now be solo mining!

***
### Solo mining (building it yourself)
