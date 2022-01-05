<script>
  import dashboardData from '../../data.json'

  let selectedTimeFrame = 'weekly'
  let readableTimeFrame = 'Week'

  const setTimeFrame = (e) => {
    let timeFrame = e.target.value

    switch (timeFrame) {
      case 'daily':
        selectedTimeFrame = 'daily'
        readableTimeFrame = convertToReadableTimeFrame(timeFrame)
        break
      case 'weekly':
        selectedTimeFrame = 'weekly'
        readableTimeFrame = convertToReadableTimeFrame(timeFrame)
        break
      case 'monthly':
        selectedTimeFrame = 'monthly'
        readableTimeFrame = convertToReadableTimeFrame(timeFrame)
        break
    }
  }

  const convertToReadableTimeFrame = (timeFrame) => {
    switch (timeFrame) {
      case 'daily':
        return 'Day'
      case 'weekly':
        return 'Week'
      case 'monthly':
        return 'Month'
    }
  }

  const getSvgPath = (activityTitle) => {
    switch (activityTitle) {
      case 'Work':
        return '/assets/icon-work.svg'
      case 'Play':
        return '/assets/icon-play.svg'
      case 'Study':
        return '/assets/icon-study.svg'
      case 'Exercise':
        return '/assets/icon-exercise.svg'
      case 'Social':
        return '/assets/icon-social.svg'
      case 'Self Care':
        return '/assets/icon-self-care.svg'
    }
  }

  const getSvgBackgroundColor = (activityTitle) => {
    switch (activityTitle) {
      case 'Work':
        return 'bg-cstm-primary-light-red-work'
      case 'Play':
        return 'bg-cstm-primary-soft-blue-play'
      case 'Study':
        return 'bg-cstm-primary-light-red-study'
      case 'Exercise':
        return 'bg-cstm-primary-lime-green-exercise'
      case 'Social':
        return 'bg-cstm-primary-violet-social'
      case 'Self Care':
        return 'bg-cstm-primary-soft-orange-self-care'
    }
  }
</script>

<div class="text-white font-rubik md:container md:mx-auto">
  <div class="grid grid-cols-1 md:grid-cols-4 md:gap-x-8">
    <!-- Main grid col 1 -->
    <div class="mb-6 row-span-2 md:h-full">
      <!-- Person info div -->
      <div
        class="bg-cstm-primary-blue flex md:flex-col items-center md:items-start p-10 gap-5 rounded-2xl relative top-3 md:pb-28"
      >
        <div>
          <img
            src="/assets/image-jeremy.png"
            alt="Jeremy"
            class="w-20 border-4 border-white rounded-full"
          />
        </div>
        <div class="md:pt-5">
          <p class="text-cstm-neutral-pale-blue">Report for</p>
          <h1 class="text-3xl md:text-6xl lg:text-5xl font-light">
            Jeremy Robson
          </h1>
        </div>
      </div>
      <!-- Time frame selection div -->
      <div
        class="flex md:flex-col justify-between md:items-start md:space-y-6 bg-cstm-neutral-dark-blue px-10 pt-10 pb-6 rounded-b-2xl"
      >
        <button
          value="daily"
          on:click|preventDefault={setTimeFrame}
          class={`${
            selectedTimeFrame === 'daily'
              ? 'text-white'
              : 'text-cstm-neutral-pale-blue'
          } hover:text-white`}>Daily</button
        >
        <button
          value="weekly"
          on:click|preventDefault={setTimeFrame}
          class={`${
            selectedTimeFrame === 'weekly'
              ? 'text-white'
              : 'text-cstm-neutral-pale-blue'
          } hover:text-white`}>Weekly</button
        >
        <button
          value="monthly"
          on:click|preventDefault={setTimeFrame}
          class={`${
            selectedTimeFrame === 'monthly'
              ? 'text-white'
              : 'text-cstm-neutral-pale-blue'
          } hover:text-white`}>Monthly</button
        >
      </div>
    </div>
    <!-- Main grid col 2 -->
    {#each dashboardData as dataItem}
      <div class="rounded-xl">
        <!-- SVG with background div -->
        <div
          class={`${getSvgBackgroundColor(
            dataItem.title
          )} rounded-t-2xl px-5 overflow-hidden flex justify-end items-center h-20`}
        >
          <img
            src={getSvgPath(dataItem.title)}
            alt={dataItem.title}
            width="100"
          />
        </div>
        <!-- Content div -->
        <div
          class="bg-cstm-neutral-dark-blue hover:bg-cstm-neutral-desaturated-blue cursor-pointer p-8 flex flex-col gap-5 md:gap-10 rounded-2xl relative bottom-7"
        >
          <div class="flex justify-between items-center">
            <p class="text-xl font-bold">{dataItem.title}</p>
            <img
              src="/assets/icon-ellipsis.svg"
              alt="ellipsis icon"
              class="cursor-pointer"
            />
          </div>
          <div
            class="flex md:flex-col justify-between items-center md:items-start md:gap-5"
          >
            <p class="font-light text-4xl md:text-6xl">
              {dataItem.timeframes[selectedTimeFrame].current}hrs
            </p>
            <p class="text-cstm-neutral-pale-blue">
              Last {readableTimeFrame} - {dataItem.timeframes[selectedTimeFrame]
                .previous}hrs
            </p>
          </div>
        </div>
      </div>
    {/each}
  </div>
</div>
