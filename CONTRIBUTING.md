If you want to contribute, you should preview your changes locally to see if there are any errors.
You need to install [ruby] and [bundler]. If you use fedora, you can simply run

```
sudo dnf install ruby ruby-devel rubygem-bundler rubygem-json rubygem-bigdecimal
```

You can the clone this repo, install jekyll and run it.

```bash
git clone https://github.com/rusty-snake/tricks.git
cd tricks
bundle config set --local path 'vendor/bundle'
bundle install
bundle exec jekyll serve
```

Now you can open `http://127.0.0.1:4000/` in your browser and see the results.

[ruby]: https://www.ruby-lang.org/en/documentation/installation/
[bundler]: https://bundler.io/
