load 'deploy'

role :web, "alexdymo.com"

set :keep_releases, 3

set :application, "alexdymo.com"
set :deploy_to, "/srv/www/linguistics.mk.ua"
set :deploy_via, :copy_with_remote_cache

set :repository, File.join(File.expand_path(File.dirname(__FILE__)), '_site')
set :scm, :none

after "deploy", "deploy:cleanup"

namespace :deploy do
    task :finalize_update do
        # symlink google site verification file
        run <<-CMD
            cd #{shared_path} &&
            for name in `ls google*`; do ln -nfs #{shared_path}/$name #{release_path}/; done
        CMD
    end
end

# kate: space-indent on; indent-width 4; hl ruby
