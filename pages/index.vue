<template>
  <div class="flex flex-col-reverse justify-items-center place-content-center text-center">
    <header>
      <div class="grid justify-items-center">
        <img
          src="launcher.jpg"
          class="h-72 w-auto"
          title="345 Launcher"
        />
      </div>
      <h1><span class="text-lime-500 font-sans font-semibold text-7xl">345 Launcher</span></h1>   
      <h1 class="my-6"><span class="text-gray-100 font-sans font-medium text-3xl">Advanced Minecraft Launcher</span></h1>
      <div class="grid justify-items-center margin-auto mt-6">
      <a
            v-for="(repo, index) in repos"
            :key="`repo-${index}`"
            :href="repo.html_url"
            target="_blank"
            rel="noreferrer"
            title="Click here to visit this repository"
          >
            <RepoCard
              :name="repo.name"
              :language="repo.language"
              :stars="repo.stargazers_count"
              :description="repo.description"
              class="h-full w-96"
            />
          </a>
      </div>
    </header>
 
  </div>
</template>

<script>
export default {
  data() {
    return {
      repos: [],
    
    }
  },
  async fetch() {
    const filter = ["githubuser-view", "star-charts", "devfont", "my-code-tips-cheatsheets", "abc-portfolios", "hashnode-analytics", "github-rater", "abc-gitstalk", "githubstars", "codingtips", "awesome-newsletters","cheatsheets-dev","abc-awesomesearch"]
    const { data: repos } = await this.$axios.get(
      "https://api.github.com/users/uvacoder/repos"
    )

    this.repos = repos
      ?.filter((repo) => repo.fork === false && !filter.includes(repo.name))
      ?.sort((a, b) => b?.stargazers_count - a?.stargazers_count)
  },
}
</script>
<style>

</style>
