<script>
    export let objectives = [];
    const totalObjectives = objectives.length;
    const completedObjectives = objectives.filter(
        obj => obj.status === true
    ).length;
    const progress = totalObjectives > 0 ? (completedObjectives / totalObjectives) * 100 : 0;
</script>

<div class="outer">
    <div class="inner">
        <div class="progress" style="width: {progress}%; background-color: {progress === 100 ? "#4caf50" : "#2196F3"} "></div>
    </div>
</div>

<style>
    .outer {
        margin-top: 30px; width: 100%;
    }
    .inner {
        height: 8px;
        width: 100%;
        background: #202020;
        border-radius: 4px;
        overflow: hidden;
    }
    .progress {
        height: 100%;
    }
</style>