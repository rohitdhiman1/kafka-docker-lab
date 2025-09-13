# Chef Workstation Docker Lab

This setup provides a Chef Workstation environment using Docker Compose for learning and experimenting with Chef cookbooks and recipes.

## Getting Started

1. **Start the Chef Workstation container:**
   ```sh
   docker compose -f docker-compose-chef.yml up -d
   ```

2. **Access the Chef Workstation shell:**
   ```sh
   docker exec -it chef-workstation bash
   ```

3. **Generate a sample cookbook:**
   ```sh
   chef generate cookbook my_first_cookbook
   ```

4. **Navigate to your cookbook directory:**
   ```sh
   cd my_first_cookbook
   ```

5. **Edit the default recipe:**
   Open `recipes/default.rb` and add a simple resource, for example:
   ```ruby
   file '/tmp/hello_chef.txt' do
     content 'Hello from Chef!'
   end
   ```

6. **Run Chef locally to apply the recipe:**
   ```sh
   chef-client --local-mode --runlist 'recipe[my_first_cookbook]'
   ```

## Useful Chef Commands
- `chef generate cookbook <name>`: Create a new cookbook
- `chef generate recipe <name>`: Add a new recipe to a cookbook
- `chef-client --local-mode`: Run Chef in local mode
- `knife`: Chef's command-line tool for managing cookbooks and nodes

## Data Persistence
Cookbook and Chef data are stored in the `chef_data` Docker volume, mapped to `/chef` inside the container.

## Resources
- [Chef Workstation Docs](https://docs.chef.io/workstation/)
- [Chef Getting Started](https://learn.chef.io/modules/learn-chef-workstation)

---
Feel free to experiment with Chef cookbooks and recipes in this isolated environment!
