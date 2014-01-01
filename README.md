# Webdriver::User::Agent

A helper gem to emulate populate device user agents and resolutions when using webdriver

## Installation

Add this line to your application's Gemfile:

    gem 'webdriver-user-agent'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install webdriver-user-agent

## Usage

provides a UserAgent.driver method to return a new web-driver with user agent and screen resolution mimicking a mobile device.

### Options

* :browser
	* :firefox (default)
	* :chrome
* :agent
	* :iphone (default)
	* :ipad
	* :mac
	* :android_phone
	* :android_tablet
	* :windowsxp
	* :windows7
	* :windowsphone
	* :random
* :orientation
	* :portrait (default)
	* :landscape

### Example using selenium-webdriver

	require 'selenium-webdriver'
	require 'webdriver-user-agent'
	driver = UserAgent.driver(:browser => :chrome, :agent => :iphone, :orientation => :landscape)
	driver.get 'http://tiffany.com'
	driver.current_url.should == 'http://m.tiffany.com/International.aspx'

### Example using random user agent

	require 'selenium-webdriber'
	require 'webdriver-user-agent'
	driver = UserAgent.driver(:agent => :random)
	driver.execute_script('return navigator.userAgent')
	# random agent like "Mozilla/5.0 (Windows; U; Windows NT 5.0; en-US; rv:0.9.2) Gecko/20010726 Netscape6/6.1"

### Example using watir-webdriver

	require 'watir-webdriver'
	require 'webdriver-user-agent'
	driver = UserAgent.driver(:browser => :chrome, :agent => :iphone, :orientation => :landscape)
	browser = Watir::Browser.new driver
	browser.goto 'tiffany.com'
	browser.url.should == 'http://m.tiffany.com/International.aspx'

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
