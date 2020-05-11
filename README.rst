SiteGen
=======

SiteGen is the static site generator.

Usage
=====

1. Website source files should have the following directory structure (file names are for exapmle)::

    |-- static
    |   |-- css
    |   |-- fonts
    |   `-- img
    `-- src
        |-- css
        |   `-- main.scss
        |-- pages
        |   |-- products
        |   |   `-- first.hbs
        |   `-- index.hbs
        |-- templates
        |   `-- layout.hbs
        `-- main.rs

2. Add ``sitegen`` to your ``Cargo.toml``::

    [dependencies]
    sitegen = "0.0"
    # or
    sitegen = { git = "https://github.com/noviga/sitegen" }

3. Add to your generator script::

    fn main() {
        let out_dir = "site";
        sitegen::render_css(&out_dir, "main").unwrap();
        sitegen::render_html(&out_dir, "index", "My Best Website").unwrap();
        sitegen::render_html(&out_dir, "products/first", "First Product").unwrap();
        sitegen::copy_static(&out_dir, "css").unwrap();
        sitegen::copy_static(&out_dir, "fonts").unwrap();
        sitegen::copy_static(&out_dir, "img").unwrap();
        sitegen::write_cname(&out_dir, "my-best-website.com").unwrap();
    }

4. Build the website and find it in ``site`` directory::

    cargo run

License
=======

Source code is licensed under `MIT license <LICENSE>`__.