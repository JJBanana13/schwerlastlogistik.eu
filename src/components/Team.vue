<script setup lang="ts">
import {
  Card,
  CardContent,
  CardHeader,
  CardTitle,
  CardFooter,
} from "@/components/ui/card";

import Linkedinicon from "@/icons/linkedinicon.vue";
import githubicon from "@/icons/githubicon.vue";
import xicon from "@/icons/xicon.vue";
import youtubeicon from "@/icons/youtubeicon.vue";
import Kofiicon from "@/icons/kofiicon.vue";
import Tiktokicon from "@/icons/tiktokicon.vue";
import twitchicon from "@/icons/twitchicon.vue";
import whatsappicon from "@/icons/Whatsappicon.vue";


interface TeamProps {
  imageUrl: string;
  firstName: string;
  lastName: string;
  positions: string[];
  socialNetworks: SocialNetworkProps[];
}

interface SocialNetworkProps {
  name: string;
  url: string;
}

const teamList: TeamProps[] = [
  {
    imageUrl: "https://data-node1.jjbanana13.wtf/logo/pfp/JJBanana13.webp",
    firstName: "JJBanana",
    lastName: "13",
    positions: ["Website Developer"],
    socialNetworks: [
      {
        name: "Github",
        url: "https://github.com/JJBanana13",
      },
      {
        name: "Youtube",
        url: "https://www.youtube.com/@jjbanana13",
      },
      {
        name: "KOFI",
        url: "https://ko-fi.com/jjbanana13",
      },
      {
        name: "TikTok",
        url: "https://www.tiktok.com/@jjbanana13",
      },
      {
        name: "Twitch",
        url: "https://www.twitch.tv/jjbanana13",
      },
    ],
  },
  {
    imageUrl:
      "https://data-node1.jjbanana13.wtf/logo/pfp/simon.webp",
    firstName: "Simon",
    lastName: "Jenke",
    positions: ["Inhaber"],
    socialNetworks: [
      {
        name: "TikTok",
        url: "https://www.tiktok.com/@simonjenke656",
      },
      {
        name: "Whatsapp",
        url: "https://wa.me/+4917661128856",
      },
    ],
  },

];

const socialIcon = (socialName: string) => {
  switch (socialName) {
    case "LinkedIn":
      return Linkedinicon;

    case "Github":
      return githubicon;

    case "X":
      return xicon;

    case "Youtube": // Include case for YouTube
      return youtubeicon;

    case "KOFI":
      return Kofiicon;

    case "TikTok":
      return Tiktokicon;

    case "Twitch":
      return twitchicon;
    case "Whatsapp":
      return whatsappicon;

  }
};
</script>

<template>
  <section
    id="team"
    class="container lg:w-[75%] py-24 sm:py-32"
  >
    <div class="text-center mb-8">
      <h2 class="text-lg text-primary text-center mb-2 tracking-wider">Team</h2>

      <h2 class="text-3xl md:text-4xl text-center font-bold">
        Unser gesamtes Team
      </h2>
    </div>

    <div
      class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8"
    >
      <Card
        v-for="{
          imageUrl,
          firstName,
          lastName,
          positions,
          socialNetworks,
        } in teamList"
        :key="imageUrl"
        class="bg-muted/60 dark:bg-card flex flex-col h-full overflow-hidden group/hoverimg"
      >
        <CardHeader class="p-0 gap-0">
          <div class="h-full overflow-hidden">
            <img
              :src="imageUrl"
              alt=""
              class="w-full aspect-square object-cover saturate-0 transition-all duration-200 ease-linear size-full group-hover/hoverimg:saturate-100 group-hover/hoverimg:scale-[1.01]"
            />
          </div>
          <CardTitle class="py-6 pb-4 px-6"
            >{{ firstName }}
            <span class="text-primary">{{ lastName }}</span>
          </CardTitle>
        </CardHeader>

        <CardContent
          v-for="(position, index) in positions"
          :key="index"
          :class="{
            'pb-0 text-muted-foreground ': true,
            'pb-4': index === positions.length - 1,
          }"
        >
          {{ position }}<span v-if="index < positions.length - 1">,</span>
        </CardContent>

        <CardFooter class="space-x-4 mt-auto">
          <a
            v-for="{ name, url } in socialNetworks"
            key="name"
            :href="url"
            target="_blank"
            class="hover:opacity-80 transition-all"
            :aria-label="`Visit our ${name} page`"
          >
            <component :is="socialIcon(name)" />
          </a>
        </CardFooter>
      </Card>
    </div>
  </section>
</template>
