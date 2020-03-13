# 9Anime anime downloader

There are two scripts (Anime_Downloader.py, Anime_Scraper.py) to download given anime to a directory and to extract direct download links.
Anime_Scraper.py scraper is used to collect and extract direct anime download links from 9anime.to (From its Mp4Upload server)

## Download Anime Downloader [Windows]
> Note : Currently only windows executable is provided (Linux, Mac users go to [Build from source](#Building-from-source))

Download the [Latest Relase](https://github.com/Oshan96/Anime-Downloader/releases) from here and extract the zip file

## Downloading 

First of all, Anime Downloader uses [2captcha](https://www.2captcha.com) to bypass google recaptcha, so you need to purchase one

Open settings.json and set [2captcha](https://2captcha.com/) API key in "api_key"

```json
    "api_key":"insert_2captcha_api_key"
```

*Don't have 2captcha API key? Don't worry! You can still use this to download anime. Check the "FAQ" section on [how to download if you don't have a 2captcha API key](#Q---I-don't-have-a-2captcha-API-key,-is-there-any-workaround-for-that?)*

Navigate to the extracted folder and open a cmd or powershell window from that folder and execute "anime-dl.exe" from command line.

## How to download using anime-dl?

First of all, you need to be familiar with the commands you can use with the Anime Downloader.

```
Commands List :
  -h, --help            show this help message and exit
  -u, --url             9Anime.to URL for the anime to be downloaded
  -n, --names           https://www.animefillerlist.com/ URL to retrieve episode titles
  -d, --directory       Download destination. Will use the current directory if not provided
  -s, --start           Starting episode
  -e, --end             End episode
  -c, --code            Recaptcha answer token code. Insert this if you don't have 2captcha captcha bypass api_key
  -t, --threads         Number of parrallel downloads. Will download sequencially if not provided
  -f, --filler          Whether fillers needed (True/False)
```
Above mentioned are the arguments you should use in order to download anime. 

The below [FAQ](#FAQ) section provides examples on how to download anime

## FAQ

### Q - How can I download one piece anime episodes from 10 to 20?

```bash
    ./anime-dl.exe -u https://9anime.to/watch/one-piece.ov8/169lyx -s 10 -e 20 -n https://www.animefillerlist.com/shows/one-piece 
```

Explantion of the commands used : 
1) -u https://9anime.to/watch/one-piece.ov8/169lyx  : After the "-u" the 9anime.to url for one piece anime is provided
2) -s 10    : start downloading from 10th episode (included)
3) -e 20    : end downloading at 20th episode (included)
4) -n https://www.animefillerlist.com/shows/one-piece   : Provide the animefillerlist.com url for one piece episodes list (this is required)

### Q - How can I download one piece anime episodes 30 to 70 into "D:\Anime\One Piece" folder?

```bash
    ./anime-dl.exe -u https://9anime.to/watch/one-piece.ov8/169lyx -s 10 -e 20 -n https://www.animefillerlist.com/shows/one-piece -d "D:\Anime\One Piece" 
```

Explanation of commands : 
1) -d "D:\Anime\One Piece"  : Download the episodes into "D:\Anime\One Piece" folder

### Q - How can I download bleach episodes 100 to 130 into "D:\Anime\Bleach" folder and download 4 episodes at once?

```bash
    ./anime-dl.exe -u https://9anime.to/watch/bleach.6j9/lz7wvq -s 100 -e 130 -n https://www.animefillerlist.com/shows/bleach -d "D:\Anime\Bleach" -t 4
```

Explanation of commands : 
1) -t 4  : Perform 4 downloads at once

### Q - How can I download bleach episodes 100 to 130 without filler episodes into "D:\Anime\Bleach" folder and download 3 episodes at once?

```bash
    ./anime-dl.exe -u https://9anime.to/watch/bleach.6j9/lz7wvq -s 100 -e 130 -n https://www.animefillerlist.com/shows/bleach -d "D:\Anime\Bleach" -t 4 -f False
```

Explanation of commands : 
1) -f False  : Avoid downloading filler episodes in the given range (Default : True)

### Q - I don't have a 2captcha API key, is there any workaround for that?
Answer : Yes ofcourse! If you don't have a 2captcha API key to bypass captcha, you can still download your favourite anime!
*But how?*
Follow these steps and you will be up and running in no time!

Let's try it!

> Assumptions : let's assume you want to download bleach episodes as in the previous question

Steps : 
1) Open a private window in the browser (ex: Google chrome)
2) Go to the 9anime url (Bleach page) (https://9anime.to/watch/bleach.6j9/lz7wvq)
3) Now the recaptcha will appear

![recaptcha image](docs/images/recaptcha.png)

4) Right click and open inspection mode (ctrl+shift+i for google chrome)

![inspect window](docs/images/inspect.png)
![inspect window2](docs/images/inspect2.png)

5) Solve the recaptcha appeared on page (DO NOT SUBMIT!)

![solve captcha](docs/images/solve.png)

6) Find the captcha answer from the webpage using inspector

![captcha answer](docs/images/answer.png)

Answer is the "value" of the "input" element with the id "recaptcha-token" (Find for element using this id using ctrl+f to find)
Copy the "value" of the input tag

So the value/recpacha answer is :

<i>"03AERD8Xode9TV-gFkG-7CNkllpKoiXfDKVEZ0Lu9NjGpxVv89bjwNHkS5bcfXHqKXx746tsNW_IUMhSVV7Aym-lcvdn6jd5Ggy1a28AQ_BI1K380joLpYReKB0EOjJjO2oVEUpOgtPu0fgfjxABKpI9EjrDZ0T7iSsKDPfhnXebQcZxIbAwelADkZ8m4qYojn3J_-kQyreIRCEztWyTTpm_SoNt6lIpFxG-egDFqVF6Sg7ICPp0QQrPa5UC-6pecgs_3xspg7PN48VOXGfHH4PCARIaGVL-J5CYNsesqUuZ4t_4kni9euduhtB3KCrV1_IYOhymepwczWIKKPGmze2DKVddoDBABlS8NZaxHRFAzNjjJHOhlRyblBMlmerK_Mu5N25bZeY5ZZ"</i>

Now we have what we need!

All you have to do is, add -c or --code command to the previous example's code like below

```bash
    ./anime-dl.exe -u https://9anime.to/watch/bleach.6j9/lz7wvq -s 100 -e 130 -n https://www.animefillerlist.com/shows/bleach -d "D:\Anime\Bleach" -t 4 -f False -c 03AERD8Xode9TV-gFkG-7CNkllpKoiXfDKVEZ0Lu9NjGpxVv89bjwNHkS5bcfXHqKXx746tsNW_IUMhSVV7Aym-lcvdn6jd5Ggy1a28AQ_BI1K380joLpYReKB0EOjJjO2oVEUpOgtPu0fgfjxABKpI9EjrDZ0T7iSsKDPfhnXebQcZxIbAwelADkZ8m4qYojn3J_-kQyreIRCEztWyTTpm_SoNt6lIpFxG-egDFqVF6Sg7ICPp0QQrPa5UC-6pecgs_3xspg7PN48VOXGfHH4PCARIaGVL-J5CYNsesqUuZ4t_4kni9euduhtB3KCrV1_IYOhymepwczWIKKPGmze2DKVddoDBABlS8NZaxHRFAzNjjJHOhlRyblBMlmerK_Mu5N25bZeY5ZZ
```

### Recaptcha does not appear even in private browsing. What can I do?

Answer :
> Assumptions : let's assume you want to download bleach episodes as in the previous question

This can be solved in 2 steps.

1) Run the anime-dl commands without -c/--code command (like you have a 2captcha key)
This will probably give error, but that's what we need.

2) Now try loading the recaptcha page in private browsing. It will appear!

## Building from source

- Clone the project using to your local machine

### Prerequisites

- Make sure python3 and pip3 is installed

### Installing

1) Download the dependancies using requirements.txt file

```
    pip install -r requirements.txt 
```
2) Rename settings_example.json as settings.json

3) Open settings.json and set [2captcha](https://2captcha.com/) API key in "api_key"

```json
    "api_key":"insert_2captcha_api_key"
```

> If you don't have a 2captcha API key purchased, check the "FAQ" section on [how to download if you don't have a 2captcha API key](#Q---I-don't-have-a-2captcha-API-key,-is-there-any-workaround-for-that?)

## Usage

Anime Downloader is a CLI application which takes command line arguments in execution time

To see the full available commands, run

```bash
python ./Anime_Downloader.py --help
```

```
usage: Anime_Downloader.py [-h] -u <URL> -n <TITLE_URL> [-d <DIR>] [-s <START>]
                           [-e <END>] [-c <TS_NO>] [-t <THREADS>] [-f <ISFILLER>]

Anime Downloader Command Line Tool

optional arguments:
  -h, --help            show this help message and exit
  -u, --url             9Anime.to URL for the anime to be downloaded
  -n, --names           https://www.animefillerlist.com/ URL to retrieve episode titles
  -d, --directory       Download destination. Will use the current directory if not provided
  -s, --start           Starting episode
  -e, --end             End episode
  -c, --code            Recaptcha answer token code. Insert this if you don't have 2captcha captcha bypass api_key
  -t, --threads         Number of parrallel downloads. Will download sequencially if not provided
  -f, --filler          Whether fillers needed (True/False)

```
## Examples

Download One Piece episodes from 130 to 180 without filler episodes into "K:\Anime\One-Piece" folder with episode names (3 simultanious downloads a time)

```bash
    python3 ./Anime_Downloader -u https://9anime.to/watch/one-piece.ov8/169lyx -s 130 -e 180 -f False -d "F:\Anime\One-Piece" -n https://www.animefillerlist.com/shows/one-piece -t 3
```
![Result](https://i.imgur.com/gRUhQdS.png)

## Authors

* **Oshan Mendis** - *Author* - [Oshan96](https://github.com/Oshan96)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Disclaimer

This software has been developed only for educational purposes by the [Author](https://github.com/Oshan96). By no means this encourage content piracy. Please support original content creators!