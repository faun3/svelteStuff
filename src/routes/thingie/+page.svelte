<script lang="ts">
  let artists = [
    {
      name: "Fleetwood Mac",
      albums: [
        {
          name: "Tango In The Night",
          year: 1987,
          tracks: [
            { title: "Big Love", length: "3:37" },
            { title: "Seven Wonders", length: "3:38" },
            { title: "Everywhere", length: "3:43" },
            { title: "Caroline", length: "3:50" },
            { title: "Tango In The Night", length: "3:56" },
            { title: "Mystified", length: "3:08" },
          ],
        },
      ],
    },
  ];

  import Artist from "../../components/Artist.svelte";
  import Album from "../../components/Album.svelte";
</script>

{#each artists as artist}
  <Artist artistName={artist.name} />
  {#each artist.albums as album}
    <Album
      albumName={album.name}
      albumYear={album.year}
      albumTracks={album.tracks}
    />
  {/each}
{/each}
