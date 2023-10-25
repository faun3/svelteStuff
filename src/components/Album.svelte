<script lang="ts">
  type TTrack = {
    title: string;
    length: string;
  };
  export let albumName: string;
  export let albumYear: number;
  export let albumTracks: TTrack[];
</script>

<div>
  <span>{albumName}</span>
  <span> - Released in {albumYear}</span>
  <ul>
    {#each albumTracks as track}
      <li>
        {track.title} - {track.length}
      </li>
    {/each}
  </ul>
</div>
