> - [session](http://www.galitein.com/session-management-via-puppeteer/) managment
    watch for added file to read url from and add to queue to execute
> - [session](https://kth.instructure.com/courses/11/pages/running-a-second-puppeteer-script-using-the-same-session-cookies)
    save the user data and all cookies and loads it inother puppeteer instance
> - [same](https://stackoverflow.com/questions/57987585/puppeteer-how-to-store-a-session-including-cookies-page-state-local-storage) as kth uses "useDataDir"

plan = combine use data dir and code injection and have sessions ready on all proxies. and run code to swap between.

[Migrate](https://www.checklyhq.com/guides/puppeteer-to-playwright/) to playwright use [chrome](https://playwright.dev/python/docs/browsers#google-chrome--microsoft-edge) browser for codec 

get commandline input to enter when capatcha is done then run email verif stuff


        const browser = await firefox.launch({
            headless: false,
            proxy: {
            server: 'http://45.13.31.218',
            username: proxyfish154,
            password: darkdark,
            },
        });

         45.13.31.218
         proxyfish154 darkdark