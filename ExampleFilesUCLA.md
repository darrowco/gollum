[[_TOC_]]

[my internal link][internal-ref] 

# Example Files for Behat at UCLA

<center><div class="toc">
  <font size="+1"><b>
    Minimal Files for Operation<br>
  </b></font>
</div></center>

> ##composer.json
```
{
    "require": {
        "behat/behat": "^3.1",
        "behat/mink": "^1.7",
        "behat/mink-extension": "^2.2",
        "behat/mink-goutte-driver": "^1.2",
        "behat/mink-selenium2-driver": "^1.3"
    }
}
```

> ##behat.yml<br>
```
default:
    extensions:
        Behat\MinkExtension:
            base_url: http://library.ucla.edu
            browser_name: firefox
            sessions:
                goutte: # fast, CLI, browser, no javascript support
                    goutte: ~
                selenium2: # fast, CLI, opens up a browser
                    selenium2: ~
```

> ##FeatureContext.php
```
<?php

use Behat\Behat\Context\Context;
use Behat\Behat\Context\SnippetAcceptingContext;
use Behat\Gherkin\Node\PyStringNode;
use Behat\Gherkin\Node\TableNode;
use Behat\MinkExtension\Context\MinkContext;

class FeatureContext extends MinkContext
{
}
```

> ##test.feature
```
Feature: Book search
  In order to find books on library website
  As a Library user
  I need to be able to use Library services
  @javascript
  Scenario:
    Given I go to "http://library.ucla.edu/"
    And I fill in "Site Search" with "books"
    And I press "Search"
    Then I should see ""
```

> ##Output
```
darrowco@ubuntu:~/tests$ vendor/bin/behat --config behat.yml features/test.feature
Feature: Book search
  In order to find books on library website
  As a Library user
  I need to be able to use Library services

  @javascript
  Scenario:                                  # features/test.feature:6
    Given I go to "http://library.ucla.edu/" # FeatureContext::visit()
    And I fill in "Site Search" with "books" # FeatureContext::fillField()
    And I press "Search"                     # FeatureContext::pressButton()
    Then I should see ""                     # FeatureContext::assertPageContainsText()

1 scenario (1 passed)
4 steps (4 passed)
0m8.18s (13.07Mb)
darrowco@ubuntu:~/tests$ 
```

***

# Local HTML, files images, downloads

* [Local Dir Contents - HTML, Files,  Images, downloads](http://localhost:4567/pages/ExampleFilesUCLA/)

# Remote Links from Desktop Shortcuts

* [Display List of Links from Desktop Shortcuts](http://localhost:4567/links)

* [Search Firefox Bookmarks](firefox -chrome chrome://browser/content/places/places.xul)

* <chrome://browser/content/places/places.xul>

* [Edit](edit/Behat) (move to footer)
