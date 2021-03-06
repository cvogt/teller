# Happy Melly Teller
**Happy Melly Teller** is a web system which supports [Happy Melly](http://happymelly.com)'s
ecosystem and perfectly suits for any business or non-profit organization
with similar network structure.

The platform allows to manage information about people, organizations, brands,
licensees and so on. It also provides REST API for retrieving these objects
from third-party apps and websites.

## How to install and run
### Pre-requisites

1. Install Java JDK 1.7
2. Download and install Play framework
    * [http://www.playframework.com/download](http://www.playframework.com/download)
    * [http://www.playframework.com/documentation/2.1.2/Installing](http://www.playframework.com/documentation/2.1.2/Installing)
3. Download/install and start MySQL
4. Create the database and user:
    * `create database happymelly;`
    * `grant all on happymelly.* TO 'melly'@'localhost' identified by 'shum' with grant option;`
5. Create and setup Twitter application
    * Create a new application on [https://dev.twitter.com](https://dev.twitter.com)
    * Add callback URL `http://127.0.0.1:9000/authenticate/twitter`
    * Set checkbox **Allow this application to be used to Sign in with Twitter**

### Application

1. Clone the repo
2. Run the application
    * `cd teller`
    * `TWITTER_KEY=[your app consumer key] TWITTER_SECRET=[your app consumer secret] play run`
3. Open the application in a web browser and set up database
    * open [http://localhost:9000](http://localhost:9000)
4. Update database (it's required to give you an access by your twitter account)
    * `update PERSON set TWITTER_HANDLE="[your twitter id]" where TWITTER_HANDLE="happy_melly";`
    * `insert into USER_ACCOUNT (PERSON_ID, TWITTER_HANDLE, ROLE) select ID, TWITTER_HANDLE, 'admin' from PERSON where lower(TWITTER_HANDLE) = '[your twitter id]';`
5. Time to log in, pal!

## I have an idea/I want report a bug
Please, [open an issue](https://github.com/HappyMelly/teller/issues), provide as
much related information as possible and stay tuned :).

## I want to help
Check [notes for contributors](https://github.com/HappyMelly/teller/blob/master/CONTRIBUTING.md)

## License
Happy Melly Teller is licensed under [GNU General Public License v.3](http://www.gnu.org/copyleft/gpl.html)

