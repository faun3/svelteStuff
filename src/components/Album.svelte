<script lang="ts">
  type TTrack = {
    title: string;
    length: string;
  };
  // anything with "export" in front of it becomes a component prop
  export let albumName: string;
  export let albumYear: number;
  export let albumTracks: TTrack[];
</script>

<div>
  <span class="album-name">{albumName}</span>
  <span class="album-year"> - Released in {albumYear}</span>
  <ul class="album-list">
    {#each albumTracks as track}
      <li>
        {track.title} - {track.length}
      </li>
    {/each}
  </ul>
</div>
