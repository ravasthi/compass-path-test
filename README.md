# Example Application for Asset Recompilation Issue

This is a simple Compass-based Rails application (using Ruby 1.9.3 and Rails 3.2) that contains partial stylesheets in subdirectories of `app/assets/stylesheets` which have been added to the Compass configuration using the `additional_import_paths` setting. Though initial asset compilation works and the partials in subdirectories get picked up correctly, subsequent changes to those files do not trigger on-the-fly Sass recompilation in development mode. This does not change even across app restarts, and the only way that assets get recompiled is by manually changing the `config.assets.version` setting in `application.rb`.

I have been able to find a workaround: adding explicit paths to the partial imports in `application.scss`. Instead of

    @import "colors";

do

    @import "basics/colors";


