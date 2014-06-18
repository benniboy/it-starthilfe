./bin/test -s Products.CMFPlone -t "Scenario Rename" --all
>>> from interlude import interact; interact(locals())


robottest run in debug if something fails 

in der importing section folgendes einfügen:
Register Keyword To Run On Failure  Debug


oder wenn man es aus ./bin bla aufruft so:
ROBOT_SELENIUM_RUN_ON_FAILURE=Debug bin/test -s zlag.mediadb -t "selection should be persistent after logout and login"

ROBOT_SELENIUM_RUN_ON_FAILURE=Debug bin/test
