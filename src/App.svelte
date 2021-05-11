<script>
    import Monaco from './components/monaco/monaco-editor.svelte';
    import SplitPane from './SplitPlane.svelte';
    export let name;
    export let orientation = 'columns';
    export let fixed = false;
    export let fixedPos = 50;
    let monaco;
    window['monaco'] = monaco;

    name = "Kevin"
  
  </script>

<style>
    main {
        text-align: center;
        padding: 1em;
        max-width: 240px;
        margin: 0 auto;
        height: 100%;
    }
    h1 {
        color: #ff3e00;
        text-transform: uppercase;
        font-size: 4em;
        font-weight: 100;
    }
    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
    .container {
      position: relative;
      width: 100%;
      height: 100%;
  }

  .container section {
      position: relative;
      padding: 42px 0 0 0;
      height: 100%;
      box-sizing: border-box;
  }

  .container section > :global(*):first-child {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      box-sizing: border-box;
  }

  .container section > :global(*):last-child {
      width: 100%;
      height: 100%;
  } 
</style>
    <body class="container" class:orientation>
        <main>

        
        <SplitPane
		type="{orientation === 'rows' ? 'vertical' : 'horizontal'}"
		pos="{fixed ? fixedPos : orientation === 'rows' ? 50 : 60}"
		{fixed}
	>
    <section slot=a>
            <Monaco bind:this={monaco} />
    </section>
    <section  slot=b style='height: 100%;'>
        <div>
            <div>
                <h1>Hello {name}!</h1>
            </div>
        </div>
    </section>
	</SplitPane>
</main>
</body>
  
