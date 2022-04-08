> - [session](http://www.galitein.com/session-management-via-puppeteer/) managment
    so code can be injected and just keep session alive 24/7 aka never turn off chrome session
> - [session](https://kth.instructure.com/courses/11/pages/running-a-second-puppeteer-script-using-the-same-session-cookies)
    save the user data and all cookies and loads it inother puppeteer instance
> - [same](https://stackoverflow.com/questions/57987585/puppeteer-how-to-store-a-session-including-cookies-page-state-local-storage) as kth uses "useDataDir"

plan = combine use data dir and code injection and have sessions ready on all proxies. and run code to swap between.